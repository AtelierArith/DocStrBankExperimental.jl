```
Hyperrectangle{N, VNC<:AbstractVector{N}, VNR<:AbstractVector{N}
              } <: AbstractHyperrectangle{N}
```

ハイパーレクタングルを表す型です。

[ハイパーレクタングル](https://en.wikipedia.org/wiki/Hyperrectangle)は、一次元の区間のデカルト積です。

### フィールド

  * `center` – ハイパーレクタングルの中心を表す実ベクトル
  * `radius` – ハイパーレクタングルの半径を表す実ベクトル、すなわち各座標方向に沿った幅の半分

### 例

`Hyperrectangle`型は、中心を表すベクトルと半径を表す別のベクトルを格納します。デフォルトのコンストラクタ`Hyperrectangle(c, r)`は、中心と半径をその順序で受け取ります。例えば、

```jldoctest hyperrectangle_constructor
julia> c = [-1.0, 1.0];

julia> r = [2.0, 1.0];

julia> H = Hyperrectangle(c, r)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([-1.0, 1.0], [2.0, 1.0])
```

上記のインスタンスは、次の頂点を持つハイパーレクタングルを表します：

```jldoctest hyperrectangle_constructor
julia> vertices_list(H)
4-element Vector{Vector{Float64}}:
 [1.0, 2.0]
 [-3.0, 2.0]
 [1.0, 0.0]
 [-3.0, 0.0]
```

中心と半径のゲッタ関数は`center`と`radius_hyperrectangle`です（`radius`は最小体積の外接球の半径に対応します）：

```jldoctest hyperrectangle_constructor
julia> center(H)
2-element Vector{Float64}:
 -1.0
  1.0

julia> radius_hyperrectangle(H)
2-element Vector{Float64}:
 2.0
 1.0
```

下限と上限からのコンストラクタもあり、キーワード引数`high`と`low`を使用します。次の構築は、前の段落と同じハイパーレクタングルを生成します：

```jldoctest hyperrectangle_constructor
julia> l = [-3.0, 0.0];

julia> h = [1.0, 2.0];

julia> Hyperrectangle(low=l, high=h)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([-1.0, 1.0], [2.0, 1.0])
```

デフォルトでは、コンストラクタはハイパーレクタングルの半径が非負であることを確認します。このチェックを抑制するには、コンストラクタで`check_bounds`オプションフラグを使用します。`check_bounds`が`false`に設定されている場合、矛盾する境界を持つ集合の動作は未定義です。
