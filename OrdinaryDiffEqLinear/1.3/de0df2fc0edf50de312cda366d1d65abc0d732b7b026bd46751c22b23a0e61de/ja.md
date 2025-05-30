```julia
LinearExponential(; krylov = :off,
                    m = 10,
                    iop = 0)
```

半線形ODEソルバー 線形で時間に依存しない問題の正確な解の公式。

### キーワード引数

  * `krylov`:

      * `:off`: 演算子を事前にキャッシュします。演算子Aに対してMatrix(A)メソッドが定義されている必要があります。
      * `:simple`: 固定サブスペースサイズmを持つ単純なKrylov近似を使用します。
      * `:adaptive`: 内部タイムステッピングを伴う適応Krylov近似を使用します。
  * `m`: `krylov=:simple`の場合はKrylovサブスペースのサイズを制御し、`krylov=:adaptive`の場合は初期サブスペースサイズを制御します。
  * `iop`: ゼロでない場合、不完全直交化手続きの長さを決定します。線形演算子/ヤコビ行列がエルミートの場合、ランチョスアルゴリズムが常に使用され、IOP設定は無視されます。

## 参考文献

@book{strogatz2018nonlinear,     title={Nonlinear dynamics and chaos: with applications to physics, biology, chemistry, and engineering},     author={Strogatz, Steven H},     year={2018},     publisher={CRC press}}
