```
destripe!(obs_list, destriping_data::DestripingData{T,O}; comm, unseen, callback) where {T <: Real, O <: Healpix.Order}
```

`obs_list`内のTODにデストライピングアルゴリズムを適用します。結果は[`DestripingData`](@ref)型の`destriping_data`に返され、ベースライン、I/Q/Uマップ、重みマップなどが含まれます。

パラメータは以下の制約を満たす必要があります：

  * `obs_list`は`N`の[`Observation`](@ref)オブジェクトの配列でなければなりません；
  * `destriping_data`は[`DestripingData`](@ref)オブジェクトでなければなりません。[`reset_maps!`](@ref)を使用して初期化されている必要はありません。

オプションのキーワードは以下の意味とデフォルト値を持ちます：

  * `comm`はMPIコミュニケーターオブジェクトであり、MPIが使用されていない場合は`nothing`です。
  * `unseen`は、観測されていないマップのピクセルに使用される値です。デフォルトは`missing`であり、他の妥当な値は`nothing`と`NaN`です。
  * `callback`は`nothing`（デフォルト）またはCGアルゴリズムが開始される前に呼び出され、その後は毎回のイテレーションで呼び出される関数です。デストライパーの進行状況を監視したり、中間結果をデータベースやファイルに保存するために使用できます。この関数は`destriping_data`をパラメータとして受け取ります。

この関数はJuliaの`Logging`モジュールを使用します。したがって、診断メッセージの出力を通常通り有効にできます。以下の例を考慮してください：

```julia
global_logger(ConsoleLogger(stderr, Debug))

# このコマンドは大量の出力を生成します…
destripe!(...)
```
