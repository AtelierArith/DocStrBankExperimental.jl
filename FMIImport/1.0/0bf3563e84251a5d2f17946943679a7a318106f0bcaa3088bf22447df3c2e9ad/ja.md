```
fmi3GetIntervalFraction!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, intervalCounters::AbstractArray{fmi3UInt64}, resolutions::AbstractArray{fmi3UInt64}, qualifiers::fmi3IntervalQualifier)
```

fmi3GetIntervalFractionは次のクロックティックまでの間隔を取得します。

入力クロックに対しては、この関数を呼び出して次のアクティベーション間隔を照会することが許可されています。変化する非周期クロックの場合、この関数はこのクロックがアクティブになったすべてのイベントモードで呼び出す必要があります。カウントダウン非周期クロックの場合、この関数はすべてのイベントモードで呼び出す必要があります。クロック間隔はfmi3UpdateDiscreteStates（遅くとも）で計算されるため、この関数はfmi3UpdateDiscreteStatesの後に呼び出す必要があります。fmi3IntervalQualifiersに関する情報は、?fmi3IntervalQualifierを呼び出してください。

# TODO 引数

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準のFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::AbstractArray{fmi3ValueReference}`: 引数 `vr` は、照会される変数を定義する「ValueReference」と呼ばれる `nvr` 値ハンドルのAbstractArrayです。
  * `nvr::Csize_t`: 引数 `nvr` は `vr` のサイズを定義します。
  * `intervalCounters::AbstractArray{fmi3UInt64}`:
  * `resolutions::AbstractArray{fmi3UInt64}`:
  * `qualifiers::fmi3IntervalQualifier`:

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: 物事は完全に正しくはないが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.9. クロック

[`fmi3GetIntervalFraction!`](@ref) も参照してください。
