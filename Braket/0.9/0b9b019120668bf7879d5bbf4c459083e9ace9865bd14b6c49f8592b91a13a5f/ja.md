```
LocalSimulator(backend::Union{String, AbstractBraketSimulator})
```

ローカルで実行される量子シミュレーターであり、回路をクラウドに送信してオンデマンドで実行するのではなく、*ローカル*で実行されます。`LocalSimulator`は、[`_simulator_devices`](@ref Braket._simulator_devices)に登録されたシミュレーターのバックエンドを一意に識別する`String`の形式のハンドル、またはすでにインスタンス化されたシミュレーターオブジェクトをバックエンドとして作成する必要があります。

`LocalSimulator`は、必要に応じて独自の[`simulate`](@ref)メソッドを実装するべきです。単一のタスクまたはタスクバッチを処理できます。
