```
in_set_string(mode::MIME, set)
```

`set`への所属を表す`String`を、印刷モード`mode`を使用して返します。

## 拡張

JuMPの拡張は、新しい`set`タイプのためにこのメソッドを拡張し、印刷の可読性を向上させることがあります。

## 例

```jldoctest
julia> in_set_string(MIME("text/plain"), MOI.Interval(1.0, 2.0))
"∈ [1, 2]"
```
