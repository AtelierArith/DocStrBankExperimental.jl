```
fmi2GetFMUstate!(c::FMU2Component, FMUstate::Ref{fmi2FMUstate})
```

内部のFMU状態のコピーを作成し、このコピーへのポインタを返します。

# 引数

  * `str::FMU2Component`: FMI 2.0.2標準でインスタンス化されたFMUのインスタンスを表す可変構造体。
  * `FMUstate::Ref{fmi2FMUstate}`: エントリ時に`FMUstate == NULL`の場合、新しい割り当てが必要です。`FMUstate != NULL`の場合、`FMUstate`は以前に返された`FMUstate`を指しており、それ以降は変更されていません。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.24]: 2.1.7 変数値の取得と設定

[`fmi2GetFMUstate!`](@ref)も参照してください。
