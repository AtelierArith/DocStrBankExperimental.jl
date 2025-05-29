```julia
setposition!(
    tm::TBModel,
    R::AbstractVector{<:Integer},
    n::Int64,
    m::Int64,
    α::Int64,
    pos::Number;
    position_tolerance::Real=1.0e-4
)
```

⟨0n|$r_α$|Rm⟩ を `pos` に設定します `tm` のために。重なり行列は、このメソッドが呼び出される前に設定する必要があります、もし `tm` が直交していない場合。

`position_tolerance` は、値が `tm.site_positions`（存在しない場合を除く）と互換性があるかどうかを確認するために使用されます。
