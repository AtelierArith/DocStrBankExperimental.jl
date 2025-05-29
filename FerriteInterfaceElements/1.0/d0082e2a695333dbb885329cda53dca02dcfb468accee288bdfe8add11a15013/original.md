```
InterfaceCell(here::AbstractCell, there::AbstractCell) <: AbstractCell
```

An `InterfaceCell` is a cell based on two cells of lower dimension representing the two facets. The two base cells need to be of the same type and the order of nodes needs to match, e.g.:

```
1---2 "here"
4---3 "there"
InterfaceCell(Line((1,2)), Line((4,3)))
```

# Fields

  * `here::AbstractCell`: cell representing the facet "here"
  * `there::AbstractCell`: cell representing the facet "there"
  * `nodes`::NTuple: tuple with all node indices in appropriate order: vertex nodes "here", vertex nodes "there", facet nodes "here", ...
