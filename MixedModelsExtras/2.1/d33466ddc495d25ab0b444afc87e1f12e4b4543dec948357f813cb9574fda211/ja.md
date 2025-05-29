```
shrinkagetables(m::MixedModel{T},
                θref::AbstractVector{T}=(isa(m, LinearMixedModel) ? 1e4 : 1) .*
                                        m.optsum.initial;
                uscale=false) where {T}
```

混合モデルからのOLS推定値からBLUPへの変化のTables.jlテーブルのNamedTupleを返します。

NamedTupleの各エントリは、単一のグルーピング項に対応します。

!!! warning
    この関数は、一時的に渡されたモデルを変更して元の形に戻すため、**スレッドセーフ**ではありません。

