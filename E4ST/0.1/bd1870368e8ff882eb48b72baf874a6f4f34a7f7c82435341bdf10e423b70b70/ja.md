```
Retrofit <: Modification
```

レトロフィットのための抽象スーパタイプ。次のインターフェースを実装する必要があります：

  * (必須) [`can_retrofit(ret::Retrofit, gen::DataFrameRow)`](@ref)`-> ::Bool` - ジェネレータ行がレトロフィット可能かどうかを返します。
  * (必須) [`retrofit!(ret::Retrofit, gen)`](@ref)`-> newgen::AbstractDict` - gen テーブルに追加される新しい行を返します。
  * (オプション) [`init!(ret::Retrofit, config, data)`](@ref) - 必要な列を gen テーブルに追加するなどして、`Retrofit` でデータを初期化します。デフォルトでは何もしません。

`Retrofit` のために次のメソッドが定義されているので、`Retrofit` の任意のサブタイプに対して通常の `Modification` メソッドを定義する必要はありません - 上記のインターフェースのみを実装してください。

  * [`modify_setup_data!(ret::Retrofit, config, data)`](@ref)
  * [`modify_model!(ret::Retrofit, config, data, model)`](@ref)
