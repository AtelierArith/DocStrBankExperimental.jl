```
StatefulLuxLayer{FT}(model, ps, st)
```

!!! warning
    これは Lux.AbstractLuxLayer ではありません


内部でパラメータと状態を保存する Lux レイヤーの便利なラッパーです。これはレイヤーの内部実装で使用されることを意図しています。

## 使用例

  * [`@compact`](@ref) の内部実装では、このレイヤーが多く使用されます。
  * 状態を伝播させることが [`Box`ing](https://github.com/JuliaLang/julia/issues/15276) を伴う SciML コードベース。動機付けの例として、Neural ODE チュートリアルを参照してください。
  * Lux におけるネストされた AD サポートを促進します。この機能の詳細については、[Nested AD Manual Page](@ref nested_autodiff) を参照してください。

## 静的パラメータ

  * `FT = true` の場合、`state` の型は固定されます。すなわち、`typeof(last(model(x, ps, st))) == st` です。
  * `FT = false` の場合、状態の型は変わる可能性があります。この動作はすべてのケースで機能しますが、型の不安定性を引き起こすことになります。

## 引数

  * `model`: Lux レイヤー
  * `ps`: レイヤーのパラメータ。ユーザーが関数呼び出し時にパラメータを提供する場合は `nothing` に設定できます。
  * `st`: レイヤーの状態

## 入力

  * `x`: レイヤーへの入力
  * `ps`: レイヤーのパラメータ。オプションで、デフォルトは `s.ps` です。

## 出力

  * `y`: レイヤーの出力
