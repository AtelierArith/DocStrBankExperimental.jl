```
fmiSetTime(c::FMU2Component, t::Real)
```

新しい時間瞬間を設定し、時間に依存する変数のキャッシュを再初期化します。

# 引数

  * `c::FMU2Component`: FMU 2.0.2標準のインスタンス化されたFMUを表す可変構造体。
  * `t::Real`: 引数`t`は`Real`型の値を含みます。`t`は独立変数時間tを設定します。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.1 独立変数の提供とキャッシュの再初期化

また[`fmi2SetTime`](@ref)を参照してください。
