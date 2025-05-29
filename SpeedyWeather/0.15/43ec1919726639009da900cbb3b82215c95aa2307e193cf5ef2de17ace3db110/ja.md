```julia
set!(S::SpeedyWeather.AbstractSimulation; kwargs...) -> Any

```

シミュレーション `S` のプロパティを設定します。その他の具体的な `set!` メソッドを呼び出すための便利なラッパーです。すべての `kwargs` はこれらのメソッドに転送され、別途文書化されています。可能な `kwargs` については、それらの文書を参照してください。
