```
EdgeHoverHandler(fun)
```

Initializes `HoverHandler` for edges. Calls function

```
fun(hoverstate, idx, event, axis)
```

with `hoverstate=true` on hover and `false` at the end of hover. `idx` is the edge index.

# Example

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, edge_width = [3.0 for i in 1:ne(g)])
julia> function action(state, idx, event, axis)
           p.edge_width[][idx] = state ? 6.0 : 3.0
           p.edge_width[] = p.edge_width[] #trigger observable
       end
julia> register_interaction!(ax, :edgehover, EdgeHoverHandler(action))
```
