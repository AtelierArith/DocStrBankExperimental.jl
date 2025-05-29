```
NodeHoverHandler(fun)
```

Initializes `HoverHandler` for nodes. Calls function

```
fun(hoverstate, idx, event, axis)
```

with `hoverstate=true` on hover and `false` at the end of hover. `idx` is the node index.

# Example

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, node_size = [20 for i in 1:nv(g)])
julia> function action(state, idx, event, axis)
           p.node_size[][idx] = state ? 40 : 20
           p.node_size[] = p.node_size[] #trigger observable
       end
julia> register_interaction!(ax, :nodehover, NodeHoverHandler(action))
```
