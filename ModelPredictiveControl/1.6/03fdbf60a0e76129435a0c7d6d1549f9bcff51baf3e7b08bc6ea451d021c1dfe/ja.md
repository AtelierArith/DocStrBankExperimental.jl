```
NonLinModel{NT}(f::Function,  h::Function,  Ts, nu, nx, ny, nd=0; <keyword arguments>)
NonLinModel{NT}(f!::Function, h!::Function, Ts, nu, nx, ny, nd=0; <keyword arguments>)
```

状態空間関数 `f`/`f!` と `h`/`h!` から非線形モデルを構築します。

連続時間モデルと離散時間モデルの両方がサポートされています。デフォルトの引数は連続ダイナミクスを想定しています。離散の場合は `solver=nothing` を使用してください（詳細は拡張ヘルプを参照）。関数は次のように定義されます：

$$
\begin{aligned}
    \mathbf{ẋ}(t) &= \mathbf{f}\Big( \mathbf{x}(t), \mathbf{u}(t), \mathbf{d}(t), \mathbf{p} \Big) \\
    \mathbf{y}(t) &= \mathbf{h}\Big( \mathbf{x}(t), \mathbf{d}(t), \mathbf{p} \Big)
\end{aligned}
$$

ここで、$\mathbf{x}$、$\mathbf{y}$、$\mathbf{u}$、$\mathbf{d}$、および $\mathbf{p}$ はそれぞれ状態、出力、操作入力、測定された外乱、およびパラメータベクトルです。実際、パラメータ引数 `p` は任意のJuliaオブジェクトにすることができますが、後で変更したい場合は可変型を使用してください（例：ベクトル）。ダイナミクスが時間の関数である場合は、単に $d(t) = t$ として定義された測定された外乱を追加します。関数は次の2つの方法で実装できます：

1. **非変異関数**（アウトオブプレイス）：`f(x, u, d, p) -> ẋ` および `h(x, d, p) -> y` として定義します。この構文はシンプルで直感的ですが、より多くのメモリを割り当てます。
2. **変異関数**（インプレース）：`f!(ẋ, x, u, d, p) -> nothing` および `h!(y, x, d, p) -> nothing` として定義します。この構文は割り当てを減らし、計算負担を軽減する可能性があります。

!!! tip
    必要ない場合は、関数内の `d` または `p` 引数を `_` に置き換えてください（以下の例を参照）。


ドキュメントの残りの部分は、すべてのモデルがこの形式に最終的に到達するため、離散ダイナミクスを前提としています。オプションのパラメータ `NT` は、ベクトルの数値型を明示的に設定します（デフォルトは `Float64`）。

!!! warning
    モデルを [`NonLinMPC`](@ref)、[`ExtendedKalmanFilter`](@ref)、[`MovingHorizonEstimator`](@ref)、および [`linearize`](@ref) で使用するには、2つの関数は純粋なJuliaでなければなりません。有限差分バックエンドが使用されている場合（例：[`AutoFiniteDiff`](@extref DifferentiationInterface List)）を除きます。


さらに [`LinModel`](@ref) も参照してください。

# 引数

  * `f::Function` または `f!`: 状態関数。
  * `h::Function` または `h!`: 出力関数。
  * `Ts`: サンプリング時間（秒）。
  * `nu`: 操作入力の数。
  * `nx`: 状態の数。
  * `ny`: 出力の数。
  * `nd=0`: 測定された外乱の数。
  * `p=[]`: モデルのパラメータ（任意の型）。
  * `solver=RungeKutta(4)`: 連続ダイナミクスの離散化のための [`DiffSolver`](@ref) オブジェクト。離散時間モデルの場合は `nothing` を使用します（デフォルトは4次の [`RungeKutta`](@ref)）。
  * `jacobian=AutoForwardDiff()`: [`linearize`](@ref) が呼び出されたときの `AbstractADType` バックエンド。詳細は [`DifferentiationInterface` doc](@extref DifferentiationInterface List) を参照してください。

# 例

```jldoctest
julia> f!(ẋ, x, u, _ , p) = (ẋ .= p*x .+ u; nothing);

julia> h!(y, x, _ , _ ) = (y .= 0.1x; nothing);

julia> model1 = NonLinModel(f!, h!, 5.0, 1, 1, 1, p=-0.2)       # 連続ダイナミクス
NonLinModel with a sample time Ts = 5.0 s, RungeKutta(4) solver and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> f(x, u, _ , _ ) = 0.1x + u;

julia> h(x, _ , _ ) = 2x;

julia> model2 = NonLinModel(f, h, 2.0, 1, 1, 1, solver=nothing) # 離散ダイナミクス
NonLinModel with a sample time Ts = 2.0 s, empty solver and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    状態空間関数は離散ダイナミクスの場合も似ています：

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &= \mathbf{f}\Big( \mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k), \mathbf{p} \Big) \\
        \mathbf{y}(k)   &= \mathbf{h}\Big( \mathbf{x}(k), \mathbf{d}(k), \mathbf{p} \Big)
    \end{aligned}
    $$

    こちらも2つの実装方法があります：

    1. **非変異関数**：`f(x, u, d, p) -> xnext` および `h(x, d, p) -> y` として定義します。
    2. **変異関数**：`f!(xnext, x, u, d, p) -> nothing` および `h!(y, x, d, p) -> nothing` として定義します。


```
