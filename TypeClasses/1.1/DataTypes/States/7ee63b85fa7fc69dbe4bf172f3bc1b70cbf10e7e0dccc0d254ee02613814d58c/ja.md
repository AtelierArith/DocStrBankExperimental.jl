```
putstate(x)
```

`putstate` は、与えられた値に基づいて内部状態を変更する `State` オブジェクトの標準コンストラクタです。

## 例

```jldoctest
julia> using TypeClasses

julia> mystate = @syntax_flatmap begin
         putstate(10)
         state = getstate
         @pure println("The state is $state, and should be 10")
       end;

julia> mystate()
The state is 10, and should be 10
(nothing, 10)
```
