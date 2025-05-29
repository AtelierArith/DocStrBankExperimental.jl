function get*ashp*defaults(load_served::String="SpaceHeating")

Obtains defaults for the ASHP from a JSON data file. 

inputs load*served::String – identifier of heating load served by AHSP system force*into_system::Bool – exclusively serves compatible thermal loads if true (i.e., replaces existing technologies)

returns ashp_defaults::Dict – Dictionary containing defaults for ASHP
