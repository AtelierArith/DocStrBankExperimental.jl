Base type for structs that store supplemental attributes

Required interface functions for subtypes:

  * get_internal()

Optional interface functions:

  * get_uuid()

Subtypes may contain time series. Which requires

  * `supports_time_series(::SupplementalAttribute)`

All subtypes must include an instance of ComponentUUIDs in order to track components attached to each attribute.
