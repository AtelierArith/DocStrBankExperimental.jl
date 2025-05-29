```
@if(expr)
```

Generates `v-if` Vue.js code using `expr` as the condition. [https://vuejs.org/v2/api/#v-if](https://vuejs.org/v2/api/#v-if)

### Example

```julia
julia> span("Bad stuff's about to happen", class="warning", @if(:warning))
"<span class="warning" v-if='warning'>Bad stuff's about to happen</span>"
```

Tentatively we now also support Julia expressions with comparison operators ```julia julia> cell(@if(:i ∉ 3:2:7)) "<div class="st-col col" v-if="!(i in [3,5,7])"></div>"

julia> row("hello", @showif(:n^2 ∉ 3:2:11)) "<div v-show="!(n ** 2 ∉ [3,5,7,9,11])" class="row">hello</div>" ````
