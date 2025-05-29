```
複素行列 A+iB の逆行列を計算します。ここで、A と B は実行列です。

2 つのバージョンがあります。バージョン #1: これは事前割り当てを行います。1M 回の評価に対して、より速く、より多くのメモリを使用します: 1.771474 秒 (14.18 M アロケーション: 4.510 GiB, 4.52% gc 時間, 6.40% コンパイル時間) 
`function complex_matrix_inversion(A, B)     inv_A_B = inv(A) * B     C = inv(A + B * inv_A_B)     D = -inv_A_B * C     return C, D end`

バージョン #2: 事前割り当てなし。1M 回の評価に対して、より遅く、より少ないメモリを使用します: 2.330454 秒 (19.00 M アロケーション: 6.512 GiB, 2.71% gc 時間) 
`function complex_matrix_inversion(A, B)         C = inv(A + B * inv(A) * B)     D = -1 .* inv(A) * B * C     return C, D end`
```
