```julia
function expr_to_tree(e::Expr)
    if e.head == :call
        return nothing
    end
    children = [expr_to_tree(arg) for arg in e.args]
    return (head = e.head, args = children)
end
```
