<template>
  <app-collapse col-title="费用筛选" default-close>
    <el-form :model="form" label-width="100px" ref="form">
    	
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="费用对象" prop="target">
            <remote-select type="member" v-model="form.target" multiple></remote-select>
          </el-form-item>
          <el-form-item label="费用生成日期" prop="create_time">
            <el-date-picker type="daterange" placeholder="请选择费用生成日期" v-model="form.create_time"></el-date-picker>
          </el-form-item>
          
          <el-form-item label="通知书发文日" prop="mail_date">
            <el-date-picker type="daterange" placeholder="请选择通知书发文日" v-model="form.mail_date"></el-date-picker>
          </el-form-item>
          <el-form-item label="付款时间" prop="pay_time">
            <el-date-picker type="daterange" placeholder="请选择付款时间" v-model="form.pay_time"></el-date-picker>
          </el-form-item>
        </el-col>

        <el-col :span="12">
        <el-form-item label="费用代码" prop="code">
          <static-select type="fee_code" v-model="form.code" multiple></static-select>
        </el-form-item>
          
          <el-form-item label="费用期限" prop="due_time">
            <el-date-picker type="daterange" placeholder="请选择费用期限" v-model="form.due_time"></el-date-picker>
          </el-form-item>
          <el-form-item label="官方绝限" prop="deadline">
            <el-date-picker type="daterange" placeholder="请选择官方绝限" v-model="form.deadline"></el-date-picker>
          </el-form-item>
          
        </el-col>
      </el-row>
      <el-row style="text-align: center;">
        <el-button @click="search(form)" type="primary" size="small">查询</el-button>
        <el-button @click="clear($refs.form)" type="danger" size="small">清空</el-button>
      </el-row>
    </el-form>
  </app-collapse>
</template>

<script>
import AppCollapse from '@/components/common/AppCollapse'
import Strainer from '@/mixins/strainer'
import FeeStatus from '@/components/form/FeeStatus'
import RemoteSelect from '@/components/form/RemoteSelect'
import StaticSelect from '@/components/form/StaticSelect'

export default {
  name: 'FeeCommonStrainer',
  mixins: [ Strainer ],
  props: ['feeType'],
  data () {
		return {      
		  form: {
        target: [],
        code: [],
        mail_date: [],
        create_time: [],
        due_time: [],
        deadline: [],
        pay_time: [],
      }
		}
  },
  watch: {},
  components: { AppCollapse, FeeStatus, RemoteSelect, StaticSelect },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>