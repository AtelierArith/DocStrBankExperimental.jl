```
function unbalanced_sinkhorn!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    tol = 1e-5,
    max_iters = 10^5,
    warn::Bool = true,
) -> NamedTuple
```

アルゴリズム1を[[SFVTP19](@ref)]に従って実装します。`a`と`b`の`dual_potential`フィールドは、最適な双対ポテンシャルを保持するように更新されます。`density`、`log_density`、および`set`フィールドは変更されません。パラメータは次のとおりです。

  * `D`: 質量の生成または破壊のコストを測定するために使用される[`AbstractDivergence`](@ref)
  * `ϵ`: 正則化パラメータ
  * `C`: `a.set` × `b.set`から実数への関数; 適用可能な場合、`C(x,y) = C(y,x)`および`C(x,x)=0`を満たす必要があります。または、例えば[`cost_matrix`](@ref)によって生成された事前計算されたコスト行列
  * `tol`: 収束許容値
  * `max_iters`: 実行する最大反復回数。
  * `warn`: 最大反復回数に達したときに警告するかどうか。

`f`と`g`、それぞれ`a`と`b`の双対ポテンシャル、実行された反復回数（`iters`）、およびプロセスの最後における最大残差（`max_residual`）を含むNamedTupleを返します。これは、双対ポテンシャルの連続する反復間の最大無限ノルムの差です。`max_iters`に達しない場合、`max_residual`が`tol`を下回ると反復が停止します。

`a`と`b`がエイリアスの場合、`a.dual_potential`および`b.dual_potential`ではなく、`f`と`g`の戻り値を使用する必要があります。
