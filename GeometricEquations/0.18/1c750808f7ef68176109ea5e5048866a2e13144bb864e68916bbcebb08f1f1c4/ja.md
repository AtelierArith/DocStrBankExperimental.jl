`SODE`: 分割常微分方程

初期値問題を定義します

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

ベクトル場 $v$、初期条件 $q_{0}$、および解 $q$ は $\mathbb{R}^{d}$ の値を取ります。ここで、ベクトル場 $v$ はベクトル場の和として与えられます

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

初期条件 $q_{0}$ を持つ動的変数 $q$ は $\mathbb{R}^{d}$ の値を取ります。

### パラメータ

  * `vType <: Union{Tuple,Nothing}`: `v` の型
  * `qType <: Union{Tuple,Nothing}`: `q` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: 各サブステップのベクトル場を計算する関数のタプル
  * `q`: 各サブステップの解を計算する関数のタプル
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切り取るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
SODE(v, invariants, parameters, periodicity)
SODE(v; invariants=NullInvariants(), parameters=NullParameters(), periodicity=NullPeriodicity())
SODE(v, q, invariants, parameters, periodicity)
SODE(v, q; invariants=NullInvariants(), parameters=NullParameters(), periodicity=NullPeriodicity())
```

### 関数定義

ベクトル場を提供する関数 `v_i` は次のインターフェースを持たなければなりません

```julia
function v_i(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

解を提供する関数 `q_i` は次のインターフェースを持たなければなりません

```julia
function q_i(q₁, t₁, q₀, t₀, params)
    q₁[1] = q₀[1] + ...
    q₁[2] = q₀[2] + ...
    ...
end
```

ここで `t₀` は現在の時間、`q₀` は現在の解ベクトル、`q₁` は時間 `t₁` における新しい解ベクトルであり、1つのサブステップを計算した結果を保持します。

関数 `v` が解を返し、各サブステップのベクトル場だけでなくなることは、分割法の使用に対する柔軟性を高めます。例えば、ベクトル場 $v_i$ を解くために別の積分器を使用することを可能にします。
