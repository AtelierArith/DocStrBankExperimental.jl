delete*node!(node; child*link*fun = new*child_link)

Delete a node and re-parent the children to its own parent.

If the node is a root and it has only one child, the child becomes the root, if it has several children, it returns an error.

`child_link_fun` is a function that takes the child node of a deleted node as input and returns its new link. The default function is [`new_child_link`](@ref), which tries to be clever considering the parent and child links. See its help page for more information. If the link shouldn't be modified, use the `link` function instead.

The function returns the parent node (or the new root if the node is a root)
