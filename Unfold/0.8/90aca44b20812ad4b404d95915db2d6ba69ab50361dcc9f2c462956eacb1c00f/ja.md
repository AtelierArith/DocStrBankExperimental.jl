```
function predict(
    uf::UnfoldModel,
    f::Vector{<:FormulaTerm},
    evts::Vector{<:DataFrame};
    overlap::Bool = true,
    kwargs...
)
```

予測された ("y_hat = X*b") `Array` を返します。

  * `uf` は `<:UnfoldModel` です
  * `f` は (ベクトルの) フォーミュラで、通常は `Unfold.formulas(uf)` ですが、フォーミュラは `effects` などによって変更できます。
  * `evts` は (ベクトルの) イベントで、モデルの (おそらく連続時間の) 予測を返すために `Unfold.events(uf)` できます。カスタムイベントでも構いません。

## kwargs:

`overlap = true` (デフォルト) の場合、`evts` の `latency` 列に基づいてオーバーラップがシミュレートされます。`!ContinuousTimeTrait` の場合は、単に X*coef が返されます。

`overlap = false` の場合、オーバーラップなしで予測を返します (モデルは `ContinuousTimeTrait` (=> 基底関数 / デコンボリューションを持つ) のみ)、`predict_no_overlap` を介して。

`keep_basis` または `exclude_basis` が定義されている場合、`predict_partial_overlap` が呼び出され、指定された (または除外されたそれぞれの) イベント/基底関数に基づいてオーバーラップを選択的に導入できます。

`epoch_to` と `epoch_timewindow`: (部分的) オーバーラップ制御された予測を計算しますが、指定された `epoch_at` イベントで返し、`epoch_timewindow` の時間 (デフォルトは基底関数から取得) をサンプルで返します。

`eventcolumn` はデフォルトの `event` とは異なる場合に指定できます。

ヒント: すべての `kwargs` は `Vector` であるか、例えば `string` 型が提供される場合は `length==1` のベクトルに入れられます。

## 出力

  * `overlap=false` の場合、3D-Array を返します
  * `overlap=true` かつ `epoch_to = nothing` (デフォルト) の場合、2D-Array を返します
  * `overlap=true` かつ `epoch_to != nothing` の場合、3D Array を返します
