```
add_noise!(client::Client, model::Union{Damping,Dephasing,Depolarising,Pauli}, params::QubitNoiseParameters)
```

この関数は量子システムにノイズを追加します。ノイズモデルはDamping、Dephasing、Depolarising、またはPauliのいずれかです。ノイズのタイプがSingleQubitでない場合、関数はエラーをスローします。その後、バックエンドで表される量子ビットの範囲を反復し、指定されたモデルとパラメータに従って各量子ビットにノイズを追加します。

# 引数

  * `client::Client`: ノイズが追加されるクライアント。
  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: 使用されるノイズモデル。
  * `params::QubitNoiseParameters`: ノイズモデルのパラメータ。

# 例

```julia
client = Client()
model = Damping()
params = QubitNoiseParameters(SingleQubit(), backend)
add_noise!(client, model, params)
```
