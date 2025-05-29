指定された時間まで状態動力学をシミュレートします。`stepto!`と同じ入力を受け取りますが、指定された時間に状態ベクトルを更新するだけでなく、この関数は各時間ステップのタイムステップ、状態値、および状態遷移行列も返します。

引数:

  * `state::EarthInertialState` 伝播する状態ベクトル
  * `time::Union{Real, Epoch}` 内部状態を伝播させる時間。実数で状態を進めるか、Epochである必要があります。

返り値:

  * `t::AbstractArray{Float64, 1}` 初期シミュレーションエポックからの経過時間をスカラーとして
  * `epc::AbstractArray{Epoch, 1}` 各タイムステップでのエポック
  * `x::AbstractArray{Float64, 2}` 各タイムステップでの状態ベクトル。時間は第二軸に沿っています
  * `Phi::AbstractArray{Float64, 2}` 状態遷移行列のスタックされた配列
