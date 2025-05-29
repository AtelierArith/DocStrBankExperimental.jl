Opaque data structure holding the whole set of parameters used to compute a routing.

# Internals

These are implementation details that could evolve at any time. Many parameters here are already documented in the main public constructor for `RoutingData`.

The first four fields are the most dependable of all of them (i.e. they are likely to stay unchanged for a long period of time):

  * `g`: topology.
  * `k`: demands.
  * `solver`.
  * `name`.

Several fields configure the solving process.

  * Some parameters are always used:

      * `model_type`.
      * `model_simplifications`. TODO: reintroduce them.
      * `timeout`.
  * Some parameters are sometimes used:

      * `sub_model_type`.
  * Some parameters are only useful for oblivious routing:

      * `model_all_traffic_matrices`: only for cutting-plane implementation.
      * `model_exact_opt_d`: only for cutting-plane implementation.
      * `model_robust_reformulation_traffic_matrices`: only for dual-reformulation implementation.
  * Some parameters are only useful for problems without uncertainty.

      * `traffic_matrix`.

Several fields configure the output process.

  * `logmessage`
  * `plot_final_results`: TODO: reintroduce.
  * `plot_each_iteration`: TODO: reintroduce.
  * `export_lps`
  * `export_lps_on_error`
  * `output_folder`

From these graphs, several data structures are derived. Some of them are lazily computed when required (hence the `mutable` aspect of this structure).

  * For path-based formulations, paths are stored and uniquely identified:

      * `paths_edges`: all the paths, represented as list of edges (Edges). Path indices are always consistent with `paths`. Used as follows: `paths_edges[path_id]` is a list of edges.
      * `demand_to_path_ids`: maps a demand (arc from source to destination) to its path IDs.
      * `path_id_to_demand`: maps a path ID to the corresponding demand.
  * In order to draw the graph, node positions are computed at most once:

      * `locs_x`: for each node, its x coordinate when drawing the graph (lazily created).
      * `locs_y`: for each node, its y coordinate when drawing the graph (lazily created).
      * `locs_f`: function that computes the two previous fields when requested. Takes a graph as input and outputs two vectors, `locs_x` and `locs_y`.

The time to create the `RoutingData` object is memorised in the `time_precompute_ms` field.
