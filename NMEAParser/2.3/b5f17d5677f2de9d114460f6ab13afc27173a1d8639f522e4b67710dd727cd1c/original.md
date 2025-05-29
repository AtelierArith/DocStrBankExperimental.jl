```
NMEAData()
```

A mutable struct that stores the last parsed NMEA messages of different types.

# Fields

  * `last_GGA::Union{Nothing, GGA}`: the last GGA message parsed, or nothing if none
  * `last_RMC::Union{Nothing, RMC}`: the last RMC message parsed, or nothing if none
  * `last_GSA::Union{Nothing, GSA}`: the last GSA message parsed, or nothing if none
  * `last_GSV::Union{Nothing, GSV}`: the last GSV message parsed, or nothing if none
  * `last_GST::Union{Nothing, GST}`: the last GST message parsed, or nothing if none
  * `last_GBS::Union{Nothing, GBS}`: the last GBS message parsed, or nothing if none
  * `last_VTG::Union{Nothing, VTG}`: the last VTG message parsed, or nothing if none
  * `last_GLL::Union{Nothing, GLL}`: the last GLL message parsed, or nothing if none
  * `last_ZDA::Union{Nothing, ZDA}`: the last ZDA message parsed, or nothing if none
  * `last_DTM::Union{Nothing, DTM}`: the last DTM message parsed, or nothing if none
