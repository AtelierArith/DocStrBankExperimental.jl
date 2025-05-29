```
AAAeigs([eltype,] nep::NEP, Z::AbstractArray{T}; [logger=0,][mmax=100,][neigs=6,][maxit=min(max(10*neigs,30),100),][shifts=Vector{T}(),][linsolvercreator=FactorizeLinSolverCreator(max_factorizations=min(length(unique(shifts)),10)),][tol=eps(real(T))*1e6,][tol_appr=eps(real(T))*1e3,][v0=Vector{T}(),][errmeasure=ResidualErrmeasure(nep),][weighted=false,][cleanup_appr=true,][tol_cln=min(eps(real(T)),tol_appr),][return_details=false,][check_error_every=10,][inner_logger=0])
```

非線形固有値問題のいくつかの固有値と固有ベクトルを `AAAeigs` アルゴリズムを使用して見つけます。

# 引数

  * `nep`: 非線形固有値問題のインスタンスは `AbstractSPMF` 型でなければなりません。
  * `Z`: nep のサンプルドメインをポイントの系列として含む配列。
  * `mmax`: AAA近似の最大次数。
  * `neigs`: 見つける固有値の数。
  * `maxit`: 総反復の最大数。
  * `shifts`: Krylov ルーチン中に使用されるシフトの L ベクトル（空 -> shift=0）
  * `tol`: 残差の許容誤差。
  * `tol_appr`: AAA近似の収束の許容誤差。
  * `v0`: 開始ベクトル。
  * `weighted`: 重み付きまたは集合値 AAA を使用するかどうか。
  * `cleanup_appr`: AAA における偽極を検出するかどうか。
  * `tol_cln`: 偽極のクリーンアップの許容誤差。
  * `return_details`: 解の詳細を返すかどうか（`AAASolutionDetails` を参照）。
  * `check_error_every`: この反復数ごとに収束/終了を確認します。
  * `inner_logger`: logger と同様に機能しますが、AAA 有理近似用です（`svAAA` を参照）。

他のパラメータについては [`augnewton`](@ref) を参照してください。

# 戻り値

  * `Λ`: サンプルセット Z 内の非線形固有値問題の固有値のベクトル。
  * `X`: 対応する固有ベクトルの行列。
  * `res`: 対応する残差。
  * `details`: 要求された場合の解の詳細（AAASolutionDetails を参照）。

# 例

```julia-repl
julia> Random.seed!(2022);
julia> nep=nep_gallery("nlevp_native_gun");
julia> m=250^2; r=300^2-200^2;
julia> Z=m-r.+2*r*rand(1000)+im*(rand(1000)*r.+sqrt(1e-13));
julia> Z=Z[(~).(imag.(Z).>sin.(acos.((real.(Z).-m)/r))*r.-sqrt(1e-13))];
julia> Z=[transpose([LinRange(m-r+1e-2,m+r-1e-2,250)' m-r.+2*r*(exp.(im*LinRange(0,pi,250)')/2 .+.5)]); Z[1:500]];
julia> shifts=r*[2/3,(1+im)/3,0,(-1+im)/3,-2/3].+m;
julia> λ,X=AAAeigs(nep,Z,shifts=shifts);
julia> [norm(compute_Mlincomb(nep,λ[i],X[:,i]))/norm(X[:,i]) for i=1:length(λ)]
6-element Vector{Float64}:
 5.282105614825289e-12
 1.675900913610527e-11
 4.971723316733914e-11
 9.437128735632508e-11
 1.2277986011104446e-10
 1.4546362158344052e-10
```

# 参考文献

  * P. Lietaert, J. Pérez, B. Vandereycken, and K. Meerbergen. 自動有理近似と非線形固有値問題の線形化。IMA 数値解析ジャーナル, 2018。
  * R. Van Beeumen, K. Meerbergen, and W. Michiels. 非線形固有値問題のためのコンパクト有理 Krylov 法。SIAM 行列解析と応用ジャーナル, 36(2):820-838, 2015。

```
