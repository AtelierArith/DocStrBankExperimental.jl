```
rh!(turtle, angle)
```

タートルを頭の軸の周りに回転させます。角度は16進数の度数でなければならず、回転は時計回りです。

## 例

```jldoctest
julia> turtle = Turtle();

julia> rh!(turtle, 45.0);
```
