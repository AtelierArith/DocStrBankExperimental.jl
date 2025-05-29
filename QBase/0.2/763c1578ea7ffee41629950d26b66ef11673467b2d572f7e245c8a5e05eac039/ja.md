```
mirror_symmetric_qubit_states( θ ::  Real ) :: Vector{State{Float64}}
```

3つのミラー対称量子ビット密度行列のセットを返します。最初の状態は $|0\rangle\langle 0|$ で、他の2つは $|0\rangle$ 軸に関して対称です。 [`mirror_symmetric_qubit_kets`](@ref) を参照してください。

入力:

  * `θ ∈ [0,π/2]`: $|0\rangle$ と $|\psi_{2/3}\rangle$ の間のヒルベルト空間の角度。
