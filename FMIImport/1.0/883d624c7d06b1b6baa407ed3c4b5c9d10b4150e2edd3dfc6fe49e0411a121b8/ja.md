```
fmi3DeSerializeFMUState!(c::FMU3Instance, serialzedState::AbstractArray{fmi3Byte}, size::Csize_t, FMUstate::Ref{fmi3FMUState})
```

バイトベクター `serializedState` を長さ `size` でデシリアライズし、FMU状態のコピーを構築し、参照 `FMUstate` の指定されたアドレスにこのコピーのポインタとしてFMU状態を格納します。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `FMUstate::fmi3FMUstate`: 引数 `FMUstate` は、実際または以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。
  * `serialzedState::AbstractArray{fmi3Byte}`: 引数 `serializedState` は、ポインタ `FMUstate` によって参照されるシリアライズされたデータのコピーを含みます。
  * `size::Ref{Csize_t}`: 引数 `size` は、`Csize_t` 型の値を安全に参照するオブジェクトで、FMUstateを格納できるバイトベクターのサイズを定義します。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: 物事は完全に正しくないが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.4 完全なFMU状態の取得と設定

また、[`fmi3DeSerializeFMUState!`](@ref)も参照してください。
