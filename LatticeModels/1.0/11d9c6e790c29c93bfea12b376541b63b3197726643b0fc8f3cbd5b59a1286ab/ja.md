```
projector(f, eig::Eigensystem)
```

対角化された演算子に適用される関数を表す `Operator` を返します。以下の式で定義されます：

$$
\hat{\mathcal{P}} = \sum_i f(A_i) |\psi_i⟩⟨\psi_i|
$$
