```
modify_setup_data!(ret::Retrofit, config, data)
```

  * [`init!(ret::Retrofit, config, data)`](@ref)を呼び出してデータを初期化します。
  * 各レトロフィットのために生産されているレトロフィットを追跡するために、`data[:retrofits]`に`Dict`を作成します。
  * `gen`テーブルの行をループします。

      * [`can_retrofit(ret::Retrofit, row)`](@ref)を介してレトロフィットできるかどうかを確認します。
      * [`retrofit!(ret::Retrofit, row)`](@ref)を介して新しいレトロフィットされた発電機を構築します。
      * シミュレーションの各年に対して新しいものを1つ構築します。
