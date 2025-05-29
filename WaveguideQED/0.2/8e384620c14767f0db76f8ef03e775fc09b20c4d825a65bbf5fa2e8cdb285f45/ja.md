```
WaveguideTransform{B1,B2,Np,idx} <: WaveguideOperator{B1,B2}
```

出力状態を変換するための演算子構造 $\ket{\psi}_{\mathrm{out}} = \mathbf{C} \ket{\tilde{\psi}}_{\mathrm{out}}$ Np は1つまたは2つの光子ルーチンをディスパッチするために使用され、idx は演算子が作用する波導のインデックスを示します。詳細は [`effective_hamiltonian`](@ref) を参照してください。

例:

```
times = 0:0.1:10
bw = WaveguideBasis(1,2,times)
C = 1/sqrt(2)*[1.0 -im;-im 1]
C_transform = WaveguideTransform(bw,C)
psi_tilde = ket(bw)
psi = C_transform*psi_tilde
```
