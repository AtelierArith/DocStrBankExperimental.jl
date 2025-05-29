線形システムの解 x を計算します：

(a₀ + a₁ * A)*x = b

初期推定 x₀ を使用します。a₀ と a₁ をデフォルト値に設定すると、システム A*x = b が解決されます。

解の精度とアルゴリズムの速度のバランスを調整するために、以下に説明するように updater キーワード引数を調整することを最初に試すことをお勧めします。

キーワード引数：

  * `nsweeps`, `cutoff`, `maxdim` など（他の MPO/MPS アップデータと同様）。
  * `updater_kwargs=(;)` - ローカルアップデータに転送されるキーワード引数を含む `NamedTuple`。この場合、`KrylovKit.linsolve` は GMRES 線形アップデータです。例えば：

    ```juli
    linsolve(A, b, x; maxdim=100, cutoff=1e-8, nsweeps=10, updater_kwargs=(; ishermitian=true, tol=1e-6, maxiter=20, krylovdim=30))
    ```

    利用可能なキーワード引数の詳細については、`KrylovKit.jl` のドキュメントを参照してください。
