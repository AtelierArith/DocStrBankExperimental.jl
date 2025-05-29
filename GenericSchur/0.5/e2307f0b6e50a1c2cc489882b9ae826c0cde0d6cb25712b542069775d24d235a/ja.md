```
eigvalscond(S::Schur,nsub::Integer) => Real
```

`S`の`nsub`個の主固有値の条件数の逆数を推定します。 (`ordschur`を使用して、関心のある部分空間を`S`の前に移動します。)

解釈の詳細については、LAPACKユーザーガイドを参照してください。
