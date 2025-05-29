```
cast_FORTRAN_format(format::String)
```

フォーマット指定子 `format` をそのフィールドに分解し、[`FORTRAN_format`](@ref) オブジェクトにキャストします。許可されるフォーマット指定子のタイプは次のとおりです: `Aw`, `Iw.m`, `Bw.m`, `Ow.m`, `Zw.m`, `Fw.d`, `Ew.dEe`, `ENw.d`, `ESw.d`, `Gw.dEe`, `Dw.dEe`。ここで、`w` は幅、`m`（オプション）は最小桁数、`d` は小数点右の桁数、`e` は指数の桁数を示します。`N`/`S`（オプション）は `E` タイプの工学的/科学的フォーマットを示します。

#### 例:

```
julia> cast_FORTRAN_format("I10")
FORTRAN_format("Iw", 'I', nothing, 10, 0, 0, 0)

julia> cast_FORTRAN_format("I10.12")
FORTRAN_format("Iw.m", 'I', nothing, 10, 12, 0, 0)

julia> F = cast_FORTRAN_format("E10.5E3")
FORTRAN_format("Ew.dEe", 'E', nothing, 10, 0, 5, 3)

julia> F.Type, F.TypeChar, F.EngSci, F.width, F.nmin, F.ndec, F.nexp
("Ew.dEe", 'E', nothing, 10, 0, 5, 3)  
```
