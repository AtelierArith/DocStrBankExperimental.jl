Returns a dict that stores commonly used pre-computed data from of the data dictionary, primarily for converting data-types, filtering out deactivated components, and storing system-wide values that need to be computed globally.

Some of the common keys include:

  * `:off_angmin` and `:off_angmax` (see `calc_theta_delta_bounds(data)`),
  * `:bus` – the set `{(i, bus) in ref[:bus] : bus["bus_type"] != 4}`,
  * `:gen` – the set `{(i, gen) in ref[:gen] : gen["gen_status"] == 1 && gen["gen_bus"] in keys(ref[:bus])}`,
  * `:branch` – the set of branches that are active in the network (based on the component status values),
  * `:arcs_from` – the set `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:branch]]`,
  * `:arcs_to` – the set `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:branch]]`,
  * `:arcs` – the set of arcs from both `arcs_from` and `arcs_to`,
  * `:bus_arcs` – the mapping `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs]])`,
  * `:buspairs` – (see `buspair_parameters(ref[:arcs_from], ref[:branch], ref[:bus])`),
  * `:bus_gens` – the mapping `Dict(i => [gen["gen_bus"] for (i,gen) in ref[:gen]])`.
  * `:bus_loads` – the mapping `Dict(i => [load["load_bus"] for (i,load) in ref[:load]])`.
  * `:bus_shunts` – the mapping `Dict(i => [shunt["shunt_bus"] for (i,shunt) in ref[:shunt]])`.
  * `:arcs_from_dc` – the set `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:dcline]]`,
  * `:arcs_to_dc` – the set `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:dcline]]`,
  * `:arcs_dc` – the set of arcs from both `arcs_from_dc` and `arcs_to_dc`,
  * `:bus_arcs_dc` – the mapping `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_dc]])`, and
  * `:buspairs_dc` – (see `buspair_parameters(ref[:arcs_from_dc], ref[:dcline], ref[:bus])`),

If `:ne_branch` exists, then the following keys are also available with similar semantics:

  * `:ne_branch`, `:ne_arcs_from`, `:ne_arcs_to`, `:ne_arcs`, `:ne_bus_arcs`, `:ne_buspairs`.
