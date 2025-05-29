```
X = L96(Float32)
```

ローレンツ1996モデルを統合します。標準パラメータ

```
L96(::Type{T}=Float64,              # RHSの数値形式
::Type{Tprog}=T;                    # 予測変数の数値形式
N::Int=10_000,                      # 時間ステップの数
n::Int=36,                          # 変数の数
X::Array{Float64,1}=zeros(36),      # 初期条件
α::Real=1.0,                        # 摩擦パラメータ
F::Float64=8.0,                     # 強制定数
s::Float64=1.0,                     # スケーリング
η::Float64=0.01,                    # X[1]での初期摂動の強さ（Xが提供されていない場合）
Δt::Float64=0.01,                   # 時間ステップ
scheme::String="RK4"                # 時間統合スキーム
output::Bool=false                  # 各時間ステップを返すか？
```

# 例

```jldoc
julia> X1 = L96(Float32);
julia> X2 = L96(Float32,n=6,Δt=0.005);
julia> X3 = L96(Float16,Float32);
```
