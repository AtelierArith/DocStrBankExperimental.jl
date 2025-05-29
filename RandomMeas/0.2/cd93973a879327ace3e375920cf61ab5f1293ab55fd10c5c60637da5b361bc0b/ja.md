```
partial_trace(shadow::AbstractShadow, subsystem::Vector{Int}; assume_unit_trace::Bool=false)
```

指定されたサブシステムの補集合に対するシャドウオブジェクトの部分トレースを計算します。

# 引数

  * `shadow::AbstractShadow`: シャドウオブジェクト。
  * `subsystem::Vector{Int}`: サブシステムを保持するために指定されたサイトインデックスのベクター（1ベース）。
  * `assume_unit_trace::Bool`（オプション）: `true`の場合、シャドウが単位トレースであると仮定します（デフォルト: `false`）。これは、因子化されたシャドウの計算を高速化することができます（「トレースアウト」されたキュービットのトレースは計算されません）。

# 戻り値

指定されたサブシステムに減少した新しいシャドウオブジェクト。

# 例

```julia
reduced_shadow = partial_trace(shadow, [1, 3])
```
