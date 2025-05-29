Generates `v-for` directive to render a list of items based on an array. [https://vuejs.org/v2/guide/list.html#Mapping-an-Array-to-Elements-with-v-for](https://vuejs.org/v2/guide/list.html#Mapping-an-Array-to-Elements-with-v-for)

`@for` supports both js expressions as String or a Julia expression with Vectors or Dicts

## Example

### Javascript

```julia
julia> p(" {{todo}} ", class="warning", @for("todo in todos"))
"""
<p v-for='todo in todos'>
    {{todo}}
</p>
"""
```

### Julia expression

```julia
julia> dict = Dict(:a => "b", :c => 4);
julia> ul(li("k: {{ k }}, v: {{ v }}, i: {{ i }}", @for((v, k, i) in dict)))
"""
<ul>
    <li v-for="(v, k, i) in {'a':'b','c':4}">
        k: {{ k }}, v: {{ v }}, i: {{ i }}
    </li>
</ul>
"""
```

Note the inverted order of value, key and index compared to Stipple destructuring. It is also possible to loop over `(v, k)` or `v`; index will always be zero-based
