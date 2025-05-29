```
aggregate(datadigraph, node_list, aggregated_node_name;
            node_fn = mean, edge_fn = mean, save_agg_edge_data = false,
            agg_edge_fn = mean, agg_edge_val = 0, node_attributes_to_add = String[]
)
```

Aggregates all the nodes in `node_list` into a single node which is called `aggregated_node_name`. If nodes have any weight/attribute values defined, these values are combined via the `node_fn` function. The default for `node_fn` is Statistics.mean which averages the data for the nodes in `node_list`. Edge data are also are also combined via the `edge_fn` when two or more nodes in the `node_list` are connected to the same node and these edges have data defined on them. The `edge_fn` also defaults to `Statistics.mean`

If edges exist between nodes in `node_list`, the data on these edges can optionally be saved on the `aggregated_node_name` node by setting `save_agg_edge_data = true`. If true, then the edge data on these edges is aggregated using `agg_edge_fn`. If the user wants to define new attribute names for this data, they can pass a vector to `node_attributes_to_add`; if no vector is defined, the data will be aggregated under the names of the `edge_data` attributes. All other nodes except the aggregated nodes will have these attributes initialized as `agg_edge_val`.
