```julia
write_tmatrix(filename, 𝐓, shape)

```

T行列を`filename`にMSTM3が期待する形式で書き込みます。

MSTM3では、`TM = 1`および`TE = 2`であり、これは`TransitionMatrices.jl`の定義とは逆です。
