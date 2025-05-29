与えられた長さのパウリ群を返します。位相はデフォルトで無視されますが、`phases=true`を設定することで含めることができます。

```jldoctest
julia> pauligroup(1)
+ _
+ X
+ Z
+ Y

julia> pauligroup(1, phases=true)
+ _
+ X
+ Z
+ Y
- _
- X
- Z
- Y
+i_
+iX
+iZ
+iY
-i_
-iX
-iZ
-iY
```
