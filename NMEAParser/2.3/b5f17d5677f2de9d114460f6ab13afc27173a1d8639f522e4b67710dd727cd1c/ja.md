```
NMEAData()
```

異なるタイプの最後に解析されたNMEAメッセージを格納する可変構造体です。

# フィールド

  * `last_GGA::Union{Nothing, GGA}`: 最後に解析されたGGAメッセージ、またはない場合はnothing
  * `last_RMC::Union{Nothing, RMC}`: 最後に解析されたRMCメッセージ、またはない場合はnothing
  * `last_GSA::Union{Nothing, GSA}`: 最後に解析されたGSAメッセージ、またはない場合はnothing
  * `last_GSV::Union{Nothing, GSV}`: 最後に解析されたGSVメッセージ、またはない場合はnothing
  * `last_GST::Union{Nothing, GST}`: 最後に解析されたGSTメッセージ、またはない場合はnothing
  * `last_GBS::Union{Nothing, GBS}`: 最後に解析されたGBSメッセージ、またはない場合はnothing
  * `last_VTG::Union{Nothing, VTG}`: 最後に解析されたVTGメッセージ、またはない場合はnothing
  * `last_GLL::Union{Nothing, GLL}`: 最後に解析されたGLLメッセージ、またはない場合はnothing
  * `last_ZDA::Union{Nothing, ZDA}`: 最後に解析されたZDAメッセージ、またはない場合はnothing
  * `last_DTM::Union{Nothing, DTM}`: 最後に解析されたDTMメッセージ、またはない場合はnothing
