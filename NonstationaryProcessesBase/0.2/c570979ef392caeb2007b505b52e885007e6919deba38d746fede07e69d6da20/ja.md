```
Process(; process=nothing, process_kwargs...)
```

指定されたシステムをシミュレートする`Process`を定義します。これは`process::Function`によって指定され、制御パラメータ、サンプリングパラメータ、ソルバーパラメータ、日付やシミュレーションIDなどのメタデータを含む任意のシミュレーションパラメータを含みます。`process_kwargs`の完全なリストについては、[`fieldguide`](@ref NonstationaryProcessesBase.fieldguide)を参照してください。`Process`は、`S = (P::Process)(;process_kwargs...)`という構文を使用して他の`Process`を作成するためにも使用でき、これはまず`P`をコピーし、その後`process_kwargs`で指定されたフィールドを更新します。
