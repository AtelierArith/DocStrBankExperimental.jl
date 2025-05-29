```
NodeDragHandler(fun)
```

Initializes `DragHandler` for Nodes. Calls function

```
fun(dragstate, idx, event, axis)
```

where `dragstate=true` during the drag and `false` at the end of the drag, the last time `fun` is triggered. `idx` is the node index.

# Example

```
julia> g = wheel_digraph(10)
julia> f, ax, p = graphplot(g, node_size=20)
julia> deregister_interaction!(ax, :rectanglezoom)
julia> function action(state, idx, event, axis)
           p[:node_pos][][idx] = event.data
           p[:node_pos][] = p[:node_pos][]
       end
julia> register_interaction!(ax, :nodedrag, NodeDragHandler(action))
```
