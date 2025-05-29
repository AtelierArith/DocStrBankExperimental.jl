```
intentplot(ibn::IBN)
intentplot!(ax, ibn::IBN)
```

Creates a graph plot of the `ibn`.

## Attributes

  * `show_routers = false`: show labels for nodes
  * `show_links = false`: show labels for links.
  * `subnetwork_view = false`: show node labels with the controller view indexing.
  * `intentidx = nothing`: highligh the passed in intent.
