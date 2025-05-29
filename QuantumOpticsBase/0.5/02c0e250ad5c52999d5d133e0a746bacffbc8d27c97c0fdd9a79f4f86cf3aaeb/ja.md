```
transition([T=ComplexF64,] mb::ManyBodyBasis, to, from)
```

演算子 $|\mathrm{to}⟩⟨\mathrm{from}|$ はモード間で粒子を移動させます。

`to` と `from` はインデックスのコレクションである可能性があることに注意してください。この場合、結果の演算子は $\ldots a^\dagger_{to_2} a^\dagger_{to_1} \ldots a_{from_2} a_{from_1}$ に等しくなります。
