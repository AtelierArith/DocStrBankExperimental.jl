```
mb03kd!(compq::AbstractChar, strong::AbstractChar, k::Integer, nc::Integer, kschur::Integer, n::AbstractVector{Int64}, ni::AbstractVector{Int64}, 
        s::AbstractVector{Int64}, select::AbstractVector{BlasInt}, t::AbstractVector{Float64}, ldt::AbstractVector{Int64}, ixt::AbstractVector{Int64}, 
        q::AbstractVector{Float64}, ldq::AbstractVector{Int64}, ixq::AbstractVector{Int64}, tol::Float64, ldwork::Integer) -> (m::Int64, info::Int64)
```

対角ブロックの順序を再配置する形式行列積

```
 T22_k^s[k] * T22_k-1^s[k-1] * ... * T22_1^s[1],                (1)
```

の長さ `k` において、一般化された周期的シュール形式で、

```
          [  T11_i  T12_i  T13_i  ]
    T_i = [    0    T22_i  T23_i  ],    i = 1, ..., k,          (2)
          [    0      0    T33_i  ]
```

ここで

  * サブ行列 `T11_i` は `ni(i+1)-by-ni(i)` であり、`s[i] = 1` の場合、または `ni(i)-by-ni(i+1)` であり、`s[i] = -1` の場合で、次元に起因する無限の固有値を含みます。
  * サブ行列 `T22_i` は `nc-by-nc` であり、コア固有値を含み、一般的にはゼロでも無限でもありません。
  * サブ行列 `T33_i` は次元に起因するゼロの固有値を含みます。

整数ベクトル `select` によって指し示される `m` 個の選択された固有値が行列列 `T22_i` の先頭部分に配置されるようにします。

`s[i] = -1` であるすべての `i` に対して `n[i] = n[i+1]` であるため、`T11_i` は無効であり、更新された直交変換行列列 `Q_1, ..., Q_k` の最初の `m` 列は同じ固有値に対応する周期的な縮小部分空間を生成します。

`compq = 'U'` または `compq = 'I'` の場合、直交因子は計算され、配列 `Q` に格納されます。したがって、`s[i] = 1` の場合、

```
           T
    Q_i(in)  T_i(in) Q_(mod(i,k)+1)(in)
                                          T 
=   Q_i(out) T_i(out)  Q_(mod(i,k)+1)(out),
```

および `s[i] = -1` の場合、

```
                      T
    Q_(mod(i,k)+1)(in)   T_i(in)   Q_i(in)
                                           T 
=   Q_(mod(i,k)+1)(out)  T_i(out)  Q_i(out).
```

詳細については、`MB03KD` の SLICOT ドキュメントを参照してください。 ```
