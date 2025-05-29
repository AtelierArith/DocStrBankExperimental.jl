```julia
generate(
    gens::AbstractArray{Crystalline.SymOperation{D}, 1};
    cntr,
    modτ,
    Nmax
) -> Crystalline.GenericGroup

```

有限の生成元 `gens` から生成された群を返します。

## キーワード引数

  * `cntr` (デフォルトは `nothing`): 原始格子ベクトルに対する操作の同値性をチェックします（`isapprox(::SymOperation, ::SymOperation, cntr::Union{Nothing, Char})` も参照）。返される群には、同値でない操作のみが含まれます。
  * `modτ` (デフォルトは `true`): 群の合成操作は、格子ベクトルに対して剰余を取ることができます（`true`）しないこともできます（`false`、例えばサイト対称群に便利）。この場合、提供された生成元も整数格子変換に対して剰余を取ります。
  * `Nmax` (デフォルトは `256`): 生成される群の最大サイズ。これは、提供された生成元のセットが *有限* 群を定義しない場合に実行を停止するためのカットオフとして本質的に設定されています（特に `modτ=false` の場合に関連します）。`Nmax` より多くの操作が生成されると、メソッドはオーバーフローエラーをスローします。
