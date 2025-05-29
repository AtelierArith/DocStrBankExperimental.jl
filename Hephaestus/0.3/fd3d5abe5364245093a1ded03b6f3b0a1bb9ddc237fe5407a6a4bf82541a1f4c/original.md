```
struct Element
```

A type representing an element in the finite element model.

  * `ID`: Identification tag
  * `node_i`: Node ($i$) of the element
  * `node_j`: Node ($j$) of the element
  * `section`: Section attached to the element
  * `material`: Material attached to the element
  * `ω`: Orientation angle of the element
  * `releases_i`: End moment releases at node ($i$) of the element
  * `releases_j`: End moment releases at node ($j$) of the element
  * `state`: Current state
