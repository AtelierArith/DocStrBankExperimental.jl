```
@gutter(size, children)
```

Sets the spacing of child elements. (We use `card()` and `prettify()` from `StippleUI` for the examples.) 

```julia
julia> row(@gutter :md [
         card("Hello", sm = 12, lg = 4)
         card("World", sm = 12, md = 8)
       ]) |> prettify |> println
<div class="row col q-col-gutter-md">
    <div class="col col-sm-12 col-lg-4">
        <q-card>
            Hello
        </q-card>
    </div>
    <div class="col col-sm-12 col-md-8">
        <q-card>
            World
        </q-card>
    </div>
</div>
```

The internal reason for this macro is that elements in a gutter need to be wrapped in div-elements as you can see above.

# Caveats

The macro can only handle children if they are explicitily written in the command. The macro cannot handle content of a variable, so `row(@gutter [c1, c2])` will fail.

Instead, you'd move the gutter macro to the definition of c1 and pass the gutter size to the parent element

```
c1 = @gutter card("Hello", sm = 2,  md = 8)
c2 = @gutter card("World", sm = 10, md = 4)

row(gutter = :md, [c1, c2])
```

If you need c1 unwrapped in a different context you'd go for manual wrapping. You can also go for a mixed approach.

```
c1 = card("Hello", sm = 2,  md = 8)
row(gutter = :md, [
    cell(c1, sm = 12, md = 8, lg = 4, xl = 12)
    @gutter card("World", sm = 12, md = 8, lg = 4, xl = 12)
])
```

Due to restrictions in the Julia macro language the macro needs to go in the first position of the expression, so

```julia
row(class = "myclass", @gutter(:md, [
    card("Hello", sm = 2,  md = 8)
    card("World", sm = 10, md = 4)
])
```

will fail.

Place the class as second argument instead

```julia
row(@gutter(:md, [
    card("Hello", sm = 2,  md = 8)
    card("World", sm = 10, md = 4)
], class = "myclass"))
```
