```
abstract type Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

微分モードが使用される抽象型。

# サブタイプ

  * [`ForwardMode`](@ref)
  * [`ReverseMode`](@ref)
  * [`ReverseModeSplit`](@ref)

# 型パラメータ

  * `ABI`: 使用するランタイム [`ABI`](@ref)
  * `ErrIfFuncWritten`: 微分された関数がクロージャであり、書き込まれた場合にエラーを発生させるかどうか。
  * `RuntimeActivity`: ランタイムアクティビティを有効にするかどうか（デフォルトはオフ）

!!! warning
    `Mode` の型パラメータは公開APIの一部ではなく、予告なしに変更される可能性があります。次のヘルパー関数を使用して変更できます：

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

