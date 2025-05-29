```
Shapley(n_perms, n_var, n_outer, n_inner)
```

  * `n_perms`: 考慮する順列の数。デフォルトは -1 で、これはすべての順列が考慮されることを意味し、したがって正確なシャプレー効果アルゴリズムが使用されます。`n_perms` が正の整数に設定されている場合、シャプレー効果のランダムバージョンが使用されます。
  * `n_var`: 各ブートストラップサンプルのサイズ
  * `n_outer`: 条件付き分散を推定するために取得されるサンプルの数
  * `n_inner`: 各 `n_outer` サンプルのサイズ

## メソッドの詳細

シャプレー効果は、機能に対する感度に基づいて各特徴に帰属を割り当てるための分散ベースの方法です。シャプレー効果は、特徴が依存している可能性があることを考慮に入れており、これはソボル指標のような以前の方法では不可能です。我々の実装では、Copulas.jlを使用して、スカラー分布としての共同入力分布を定義します。

## API

```
gsa(f, method::Shapley, input_distribution::SklarDist; batch=false)
```

### 例

```julia
using Copulas, Distributions, GlobalSensitivity

function ishi(X)
    A = 7
    B = 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

function ishi_batch(X)
    A = 7
    B = 0.1
    @. sin(X[1, :]) + A*sin(X[2, :])^2+ B*X[3, :]^4 *sin(X[1, :])
end

n_perms = -1; # -1 はすべての順列を考慮したいことを示します。n_perms > 0 を使用することもできます
n_var = 1000;
n_outer = 100;
n_inner = 3

dim = 3;
margins = (Uniform(-pi, pi), Uniform(-pi, pi), Uniform(-pi, pi));
dependency_matrix = Matrix(I, dim, dim)

C = GaussianCopula(dependency_matrix);
input_distribution = SklarDist(C,margins);

method = Shapley(n_perms=n_perms, n_var = n_var, n_outer = n_outer, n_inner = n_inner);

###### 非バッチ
result_non_batch = gsa(ishi,method,input_distribution,batch=false)
shapley_effects = result_non_batch.shapley_effects
println(shapley_effects)

###### バッチ
result_batch = gsa(ishi_batch,method,input_distribution,batch=true)
shapley_effects = result_batch.shapley_effects
println(shapley_effects)

#### 相関のある入力の例
d = 3
mu = zeros(d)
sig = [1, 1, 2]
ro = 0.9
Cormat = [1 0 0; 0 1 ro; 0 ro 1]
Covmat = (sig * transpose(sig)) .* Cormat

margins = [Normal(mu[i], sig[i]) for i in 1:d]
copula = GaussianCopula((sig * transpose(sig)) .* Cormat)
input_distribution = SklarDist(copula, margins)

result = gsa(ishi, method, input_distribution, batch = false)
```
