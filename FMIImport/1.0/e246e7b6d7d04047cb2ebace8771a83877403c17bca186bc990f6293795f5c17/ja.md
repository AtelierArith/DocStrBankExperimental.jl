```
fmi3ActivateModelPartition(c::FMU3Instance, vr::fmi3ValueReference, activationTime::AbstractArray{fmi3Float64})
```

クロックアクティベーションモード中（5.2.2を参照）に、`fmi3ActivateModelPartition`が計算された、調整可能または変化するクロックに対して呼び出された後、FMUはクロックが再びティックする時、すなわち対応するモデルパーティションが次にスケジュールされるべき時を提供します。

各`fmi3ActivateModelPartition`呼び出しは、FMUの公開されたモデルパーティションの計算に関連付けられており、したがって入力クロックに関連しています。

# TODO 引数

# 引数

  * `c::FMU3Instance`: 引数`c`は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::fmi3ValueReference`: 引数`vr`は、問い合わせる変数を定義する「ValueReference」と呼ばれる値ハンドルです。
  * `activationTime::AbstractArray{fmi3Float64}`:

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを成功裏に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 5.2.2. 状態: クロックアクティベーションモード

[`fmi3ActivateModelPartition`](@ref)も参照してください。
