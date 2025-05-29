```
fmi3SerializeFMUState!(c::FMU3Instance, FMUstate::fmi3FMUState, serialzedState::AbstractArray{fmi3Byte}, size::Csize_t)
```

ポインタ `FMUState` に参照されるデータをシリアライズし、このデータを環境によって提供される長さ `size` のバイトベクター `serializedState` にコピーします。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。
  * `FMUstate::fmi3FMUstate`: 引数 `FMUstate` は、実際のまたは以前の時間瞬間の内部 FMU 状態を保存する FMU 内のデータ構造へのポインタです。
  * `serialzedState::AbstractArray{fmi3Byte}`: 引数 `serializedState` は、ポインタ FMUstate によって参照されるシリアライズされたデータのコピーを含みます。
  * `size::Ref{Csize_t}`: 引数 `size` は、`Csize_t` 型の値を安全に参照するオブジェクトであり、FMUstate を格納できるバイトベクターのサイズを定義します。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙体であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.4. 完全な FMU 状態の取得と設定

また [`fmi3SerializeFMUState!`](@ref) を参照してください。
