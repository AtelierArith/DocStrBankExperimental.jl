A macro for extracting fields from an object.  For example, instead of a statement like

```
(obj.a + obj.b)^obj.c
```

it is more readable if we first locally bind the variables

```
a = obj.a
b = obj.b
c = obj.c

(a + b)^c
```

Using the `@getfield` marco, this becomes

```
@getfield obj (a, b, c)

(a + b)^c
```

We can also locally assign different names to the binding

```
@getfield obj (a, b, c) (α, β, γ)
(α + β)^γ
```
