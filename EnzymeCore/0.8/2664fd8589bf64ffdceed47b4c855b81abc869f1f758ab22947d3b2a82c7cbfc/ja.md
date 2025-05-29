```
struct ReverseMode{
    ReturnPrimal,
    RuntimeActivity,
    ABI,
    Holomorphic,
    ErrIfFuncWritten
} <: Mode{ABI,ErrIfFuncWritten,RuntimeActivity}
```

逆モード微分のための[`Mode`](@ref)のサブタイプ。

# 型パラメータ

  * `ReturnPrimal`: 拡張前方パスからの原始戻り値を返すかどうか。
  * `Holomorphic`: 複素結果関数がホロモルフィックであり、`d/dz`を計算すべきかどうか。
  * その他のパラメータ: [`Mode`](@ref)を参照。

!!! warning
    `ReverseMode`の型パラメータは公開APIの一部ではなく、予告なしに変更される可能性があります。代わりに以下の具体的なインスタンスのいずれかを使用してください：

      * [`Reverse`](@ref)
      * [`ReverseWithPrimal`](@ref)
      * [`ReverseHolomorphic`](@ref)
      * [`ReverseHolomorphicWithPrimal`](@ref)

    次のヘルパー関数を使用して変更できます：

      * [`WithPrimal`](@ref) / [`NoPrimal`](@ref)
      * [`set_err_if_func_written`](@ref) / [`clear_err_if_func_written`](@ref)
      * [`set_runtime_activity`](@ref) / [`clear_runtime_activity`](@ref)
      * [`set_abi`](@ref)

