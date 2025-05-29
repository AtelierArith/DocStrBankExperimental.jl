```
struct ReverseModeSplit{
    ReturnPrimal,
    ReturnShadow,
    Width,
    RuntimeActivity,
    ModifiedBetween,
    ABI,
    ErrFuncIfWritten
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
    WithPrimal(::Enzyme.Mode)
```

[`Mode`](@ref) のサブタイプで、分割逆モード微分に使用し、[`autodiff_thunk`](@ref) およびそのバリアントで使用します。

# 型パラメータ

  * `ReturnShadow`: 拡張前方からのシャドウ戻り値を返すかどうか。
  * `Width`: バッチサイズ（自動的に導出するには `0` を選択）
  * `ModifiedBetween`: 各引数の「修正された間」の状態の `Tuple`（自動的に導出するには `true` を選択）。
  * その他のパラメータ: [`ReverseMode`](@ref) を参照

!!! warning
    `ReverseModeSplit` の型パラメータは公開APIの一部ではなく、予告なしに変更される可能性があります。代わりに以下の具体的なインスタンスのいずれかを使用してください:

      * [`ReverseSplitNoPrimal`](@ref)
      * [`ReverseSplitWithPrimal`](@ref)

    次のヘルパー関数を使用してそれらを変更できます:

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)
      * [`ReverseSplitModified`](@ref), [`ReverseSplitWidth`](@ref)

