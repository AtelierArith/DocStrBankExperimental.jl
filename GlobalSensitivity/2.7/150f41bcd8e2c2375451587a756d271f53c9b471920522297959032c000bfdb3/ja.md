```
Morris(; p_steps::Array{Int, 1} = Int[], relative_scale::Bool = false,
            num_trajectory::Int = 10,
            total_num_trajectory::Int = 5 * num_trajectory, len_design_mat::Int = 10)
```

  * `p_steps`: 各方向のステップサイズのための$\Delta$のベクトル。必須。
  * `relative_scale`: 基本的な効果は、パラメータが範囲[0,1]にあると仮定して計算されますが、これは常に当てはまるわけではないため、スケーリングを使用してより情報量の多いスケール効果を得ます。デフォルトはfalseです。
  * `total_num_trajectory`, `num_trajectory`: 生成される設計行列の総数であり、その中から最も広がりのあるnum_trajectory行列が計算に使用されます。
  * `len_design_mat`: 設計行列のサイズ。

## メソッドの詳細

モリス法は、モリスのOAT法としても知られ、OATは「One At a Time」の略で、以下のステップで説明できます。

我々は「基本的な効果」として知られる局所感度測定を計算します。これは、1つのパラメータを変更したときのモデルの出力の摂動を測定することによって計算されます。

$$
EE_i = \frac{f(x_1,x_2,..x_i+ \Delta,..x_k) - y}{\Delta}
$$

これらは、分析において広範な「広がり」のパラメータ空間が探求され、考慮されるように選ばれた入力のさまざまな点で評価され、近似的なグローバル重要度測定を提供します。これらの基本的な効果の平均と分散が計算されます。平均の高い値は、パラメータが重要であることを示し、高い分散は、その効果が非線形であるか、他の入力との相互作用の結果であることを示します。この方法は、相互作用からの寄与とパラメータの個別の寄与を別々に評価せず、すべての相互作用とその個別の寄与を考慮した各パラメータの効果を提供します。

## API

```
gsa(f, method::Morris, p_range::AbstractVector; batch = false,
         rng::AbstractRNG = Random.default_rng(), kwargs...)
```

### 例

イシガミ関数に対するモリス法

```julia
using GlobalSensitivity

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

lb = -ones(4)*π
ub = ones(4)*π

m = gsa(ishi, Morris(num_trajectory=500000), [[lb[i],ub[i]] for i in 1:4])
```
