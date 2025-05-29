```
new_child_link(node)
```

Compute the new link of the child node when deleting a parent node. The rule is to give the child node link of its parent node that is deleted, except when the parent was following its own parent.

The node given as input is the child node here.

The rule is summarized in the following table:

| Deleted node link | Child node link | New child node link | warning |
|:-----------------:|:---------------:|:-------------------:|:-------:|
|         /         |        /        |          /          |         |
|         /         |        +        |          +          | yes (1) |
|         /         |        <        |          /          |         |
|         +         |        /        |          /          | yes (2) |
|         +         |        +        |          +          |         |
|         +         |        <        |          +          |         |
|         <         |        /        |          /          |         |
|         <         |        +        |          +          |         |
|         <         |        <        |          <          |         |

The warnings happens when there is no satisfactory way to handle the new link, *i.e.* when mixing branching and change in scale.

Note that in the case (1) of the warning the first child only takes the "/" link, the others keep their links.
