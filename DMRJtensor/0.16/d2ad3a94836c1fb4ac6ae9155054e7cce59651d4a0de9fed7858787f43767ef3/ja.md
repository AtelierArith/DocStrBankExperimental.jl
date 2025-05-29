```
T = correlation(dualpsi,psi,inputoperators...[,sites=ntuple(i->1,length(inputoperators)),trail=()])
```

入力MPS `psi`に対して、タプル`inputoperators`で定義された演算子を用いて一般的な相関を計算します。`sites`コマンドは、演算子を適用するために許可されるサイトを指定します（つまり、一部の演算子は一部のサイトをスキップすることができます）し、`trail`オプションはフェルミオン符号演算子のようなトレーリング演算子を許可します。出力は、`inputoperators`のサイズに等しいランクのテンソル`T`です。

参照: [`expect`](@ref) [`correlationmatrix`](@ref)
