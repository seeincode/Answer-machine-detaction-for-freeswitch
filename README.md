# Answer-machine-detaction-for-freeswitch

Port of Asterisk answer machine detection to Freeswitch

  
  Example usage

```
  <extension name="from_sbc">
    <condition field="destination_number" expression="^485(.*)$">
      <action application="bridge" data="my_outcall=${originate {execute_on_answer='transfer AMD_APP XML public'}sofia/gateway/mycarrier/${destination_number} &park()}"/>
    </condition>
  </extension>

  <extension name="amd_app">
    <condition field="destination_number" expression="^AMD_APP$">
      <action application="amd"/>
    </condition>
  </extension>

  <extension name="amd_result_machine">
    <condition field="${amd_result}" expression="^MACHINE$">
      <action application="hangup"/>
    </condition>
  </extension>

  <extension name="amd_result_human">
    <condition field="${amd_result}" expression="^HUMAN$">
      ....
    </condition>
  </extension>

```
