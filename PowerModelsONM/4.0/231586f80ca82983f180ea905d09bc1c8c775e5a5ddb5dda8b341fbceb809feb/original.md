```
build_events(
    eng::Dict{String,<:Any};
    custom_events::Vector{Dict{String,Any}}=Dict{String,Any}[],
    default_switch_state::Union{PMD.SwitchState,String}=PMD.CLOSED,
    default_switch_dispatchable::Union{PMD.Dispatchable,Bool}=PMD.YES,
    default_switch_status::Union{Missing,PMD.Status,Int}=missing
)::Vector{Dict{String,Any}}
```

A helper function to assist in making rudamentary events data structure with some default settings for switches.

  * `eng::Dict{String,<:Any}` is the input case data structure
  * `custom_events` is a Vector of *events* that will be applied **after** the automatic generation of events based off of the `default` kwargs
  * `default_switch_state::Union{PMD.SwitchState,String}` (default: `CLOSED`) is the toggle for the default state to apply to every switch
  * `default_switch_dispatchable::Union{PMD.Dispatchable,Bool}` (default: `YES`) is the toggle for the default dispatchability (controllability) of every switch
  * `default_switch_status::Union{Missing,PMD.Status,Int}` (default: `missing`) is the toggle for the default status (whether the switch appears in the model at all or not) of every switch. If `missing` will default to the status given by the model.
