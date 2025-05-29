```
struct ForwardMode{
    ReturnPrimal,
    ABI,
    ErrIfFuncWritten,
    RuntimeActivity
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

前方モード微分のための[`Mode`](@ref)のサブタイプ。

# 型パラメータ

  * `ReturnPrimal`: 拡張前方からの原始戻り値を返すかどうか。
  * その他のパラメータ: [`Mode`](@ref)を参照

!!! warning
    `ForwardMode`の型パラメータは公開APIの一部ではなく、予告なしに変更される可能性があります。代わりに以下の具体的なインスタンスのいずれかを使用してください：

      * [`Forward`](@ref)
      * [`ForwardWithPrimal`](@ref)

    次のヘルパー関数を使用して変更できます：

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

