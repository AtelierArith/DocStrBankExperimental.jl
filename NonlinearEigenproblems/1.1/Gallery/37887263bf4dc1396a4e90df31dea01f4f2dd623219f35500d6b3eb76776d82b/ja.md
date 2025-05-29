```
 nep=nep_gallery(name)
 nep=nep_gallery(name,params)
 nep=nep_gallery(name,params;kwargs)
```

非線形固有値問題のコレクション。非線形固有値問題の例のギャラリーからNEPオブジェクトを返します。パラメータ`name`はどのNEPを選択するかを決定します。

# サポートされている問題:

以下のリストは、特定の`name`を持つNEPと関連するパラメータ（`params`）およびキーワード引数（`kwargs`）を説明します。

  * `dep0`: 一つの遅延tau = 1を持つランダム[`DEP`](@ref)で、擬似乱数生成器を使用して生成されます。   *params:* サイズ（デフォルト = 5）
  * `dep0_sparse`: 一つの遅延tau = 1を持つスパース行列のランダム[`DEP`](@ref)で、擬似乱数生成器を使用して生成されます。   *Params:* サイズ（デフォルト = 5）とフィル（デフォルト = 0.25）を決定する2つのオプションのparams
  * `dep0_tridiag`: 一つの遅延tau = 1を持つスパース三重対角行列のランダム[`DEP`](@ref)で、擬似乱数生成器を使用して生成されます。   *Params:* サイズ（デフォルト = 100）
  * `dep_symm_double`: 二重固有値を持つ[`DEP`](@ref)で、スパース対称行列と一つの遅延tau = 1を持ちます。   *Params:* サイズ（デフォルト = 100）   *Reference:* [H. Voss and M. M. Betcke, Restarting iterative projection methods for Hermitian nonlinear eigenvalue problems with minmax property, Numer. Math., 2017](https://doi.org/10.1007/s00211-016-0804-3)からの例
  * `dep_double`: λ=3πiにおける二重非半単純固有値を持つ[`DEP`](@ref)。   *Reference:* [E. Jarlebring, Convergence factors of Newton methods for nonlinear eigenvalue problems, LAA, 2012](https://doi.org/10.1016/j.laa.2010.08.045)からの例
  * `dep1`: 一つの固有値が1に等しい[`DEP`](@ref)。
  * `pep0`: 擬似乱数生成器を使用して生成されたランダム[`PEP`](@ref)   *Params:* サイズ（デフォルト = 200）
  * `pep0_sym`: 擬似乱数生成器を使用して生成されたランダム対称[`PEP`](@ref)   *Params:* サイズ（デフォルト = 200）
  * `pep0_sparse`: 擬似乱数生成器を使用して生成されたスパース行列のランダム[`PEP`](@ref)   *Params:* サイズ（デフォルト = 200）とフィル（デフォルト = 0.03）を決定する2つのオプションの`params`
  * `real_quadratic`: 実数固有値を持つ二次[`PEP`](@ref)。   *Solutions:* 問題の4つの最小固有値:   ∘ `-2051.741417993845`   ∘ `-182.101627437811`   ∘ `-39.344930222838`   ∘ `-4.039879577113`
  * `dep_distributed`: 分散遅延時間遅延システムに対応するNEP   *Reference:* [E. Jarlebring and W. Michiels and K. Meerbergen, The infinite Arnoldi method and an application to time-delay systems with distributed delays, Delay Systems - Methods, Applications and New Trends, 2012](https://doi.org/10.1007/978-3-642-25221-1_17)の例   *Solutions:* 一部の正しい固有値:   ∘ `-0.400236388049641 + 0.970633098237807i`   ∘ `-0.400236388049641 - 0.970633098237807i`   ∘ `2.726146249832675 +  0.000000000000000i`   ∘ `-1.955643591177653 + 3.364550574688863i`   ∘ `-1.955643591177653 - 3.364550574688863i`   ∘ `4.493937056300693 +  0.000000000000000i`   ∘ `-1.631513006819252 + 4.555484848248613i`   ∘ `-1.631513006819252 - 4.555484848248613i`   ∘ `-1.677320660400946 + 7.496870451838560i`   ∘ `-1.677320660400946 - 7.496870451838560i`
  * `qdep0`: 二次遅延固有値問題。  *Reference:* [S. W. Gaaf and E. Jarlebring, The infinite Bi-Lanczos method for nonlinear eigenvalue problems, SIAM J. Sci. Comput., 2017](https://doi.org/10.1137/16M1084195)
  * `qdep1`: 二次遅延固有値問題。  *Reference:* [E. Jarlebring and W. Michiels and K. Meerbergen, A linear eigenvalue algorithm for the nonlinear eigenvalue problem, Numer. Math., 2011](https://doi.org/10.1007/s00211-012-0453-0)
  * `qep_fixed_eig`: 固有値が選択された二次固有値問題。  *Params:* サイズ（デフォルト = 5）と固有値を含むベクトル（デフォルト = 一様[-1,1]）を決定する2つのオプションの`params`
  * `neuron0`: 結合ニューロンのモデリングから派生した[`DEP`](@ref)。  *Reference:* [L. P. Shayer and S. A. Campbell, Stability, bifurcation and multistability in a system of two coupled neurons with multiple time delays, SIAM J. Applied Mathematics, 2000](https://doi.org/10.1137/S0036139998344015)。これはDDE-BIFTOOLのベンチマーク例でもあります。
  * `schrodinger_movebc`: NEPは、NEP-PACKオンラインチュートリアルで説明されているシュレーディンガー方程式の離散化から派生しています。非線形性には$sinh()$、$cosh()$、および$sqrt()$が含まれます。  *Params:* オプションのパラメータは、離散化のサイズ`n`とドメインおよびポテンシャルの説明`L0`、`L1`、`α`、および`V0`です。
  * `beam`: 遅延安定化フィードバックをモデル化した[`DEP`](@ref)。A1項はランク1です。  *Params:* 行列のサイズ（デフォルト = 100）  *Reference:* [R. Van Beeumen, E. Jarlebring, and W. Michiels, A rank-exploiting infinite Arnoldi algorithm for nonlinear eigenvalue problems, 2016.](https://doi.org/10.1002/nla.2043)
  * `sine`: 多項式とサイン関数の和によって形成されたNEP。サイン項はランク1の行列係数を持ちます。  *Reference:* [R. Van Beeumen, E. Jarlebring, and W. Michiels, A rank-exploiting infinite Arnoldi algorithm for nonlinear eigenvalue problems, 2016.](https://doi.org/10.1002/nla.2043)
  * `bem_fichera`: ヘルムホルツ方程式の境界要素離散化を表します。単位立方体からなるドメインで、1つの角（フィチェラ角）が除去されています。メッシュはハードコーディングされています。   *Params:* パラメータ`N`は問題のサイズを決定します（デフォルト`N = 5`）。   *Reference:* このモデルは次の論文に基づいています:  [A boundary element method for solving PDE eigenvalue problems, M. Steinlechner, bachelor thesis, ETH Zürich, 2010](http://sma.epfl.ch/~anchpcommon/students/steinlechner.pdf) および  [Effenberger and Kressner, Chebyshev interpolation for nonlinear eigenvalue problems, BIT Numerical Mathematics, December 2012, Volume 52, Issue 4, pp 933–951](https://doi.org/10.1007/s10543-012-0381-5)
  * `dtn_dimer`: 共鳴のモデリングから派生したベッセル関数の商を持つNEP    *Params:* このNEPは2つのパラメータを取ります: `data_dir::String` と `l::Int`。`data_dir`はダウンロードされたFEM行列のディレクトリを指定します（ここで入手可能 [https://umu.app.box.com/s/b52yux3z9rcl8y0l7la22k0vi062cvu5](https://umu.app.box.com/s/b52yux3z9rcl8y0l7la22k0vi062cvu5)）。整数`l`はDtN項の数を指定します: 2l+1。   *Reference:* [J. Araujo-Cabarcas, C. Engström and E. Jarlebring, Efficient resonance computations for Helmholtz problems based on a Dirichlet-to-Neumann map, J. Comput. Appl. Math., 330:177-192, 2018](http://arxiv.org/pdf/1606.09547))

[T. Betcke, N. J. Higham, V. Mehrmann, Ch. Schröder, F. Tisseur, NLEVP: A Collection of Nonlinear Eigenvalue Problems, ACM Transactions on Mathematical Software 39(2), January 2011](https://doi.org/10.1145/2427023.2427024)で説明されているMATLABパッケージは、NEPのためのいくつかのベンチマーク問題を提供します。これらはNEP-PACKで2つの異なる方法で利用可能です。いくつかの問題のネイティブ実装（`nlevp_native_`と呼ばれる）と、別の`GalleryNLEVP`があります。ネイティブ実装が推奨されます。なぜなら、`GalleryNLEVP`はMATLABとインターフェースしているため、かなり遅くなります。

  * `nlevp_native_gun`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「gun」。   [B.-S. Liao, Z. Bai, L.-Q. Lee, and K. Ko. Nonlinear Rayleigh-Ritz iterative method for solving large scale nonlinear eigenvalue problems. Taiwan. Journal of Mathematics, 14(3):869–883, 2010](https://doi.org/10.11650/twjm/1500405872)
  * `nlevp_native_cd_player`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「cd*player」。   [Y. Chahlaoui, and P. M. Van Dooren, Benchmark examples for model reduction of linear time-invariant dynamical systems. In Dimension Reduction of Large-Scale Systems, P. Benner, V. Mehrmann, and D. C. Sorensen, Eds. Lecture Notes in Computational Science and Engineering Series, vol. 45. Springer-Verlag, Berlin, 380–392, 2005.](https://doi.org/10.1007/3-540-27909-1*24)   および   P. M. R. Wortelboer, M. Steinbuch, and O. H. Bosgra, Closed-loop balanced reduction with application to a compact disc mechanism. In Selected Topics in Identification, Modeling and Control. Vol. 9. Delft University Press, 47–58, 1996.   および   [W. Draijer, M. Steinbuch, and O. H. Bosgra, Adaptive control of the radial servo system of a compact disc player. Automatica 28, 3, 455–462. 1992.](https://doi.org/10.1016/0005-1098(92)90171-B)
  * `nlevp_native_fiber`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「fiber」。   この問題の項の1つは補間によって近似されており、常にベンチマークと一致するわけではありません。   [L. Kaufman, Eigenvalue problems in fiber optic design. SIAM J. Matrix Anal. Appl. 28, 1, 105–117, 2006.](https://doi.org/10.1137/S0895479803432708)   および   [X. Huang, Z. Bai, and Y. Su, Nonlinear rank-one modification of the symmetric eigenvalue problem. J. Comput. Math. 28, 2, 218–234, 2010](https://doi.org/10.4208/jcm.2009.10-m1002)
  * `nlevp_native_hadeler`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「hadeler」。問題は$M(λ)=(e^λ-1)B+A_0+A_2λ^2$の形です。    [Hadeler K.  P.  1967.  Mehrparametrige  und  nichtlineare  Eigenwertaufgaben. Arch.  Rational  Mech. Anal. 27, 4, 306–328.](https://doi.org/10.1007/BF00281717)
  * `nlevp_native_pdde_stability`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「pdde_stability」。   この問題は任意のサイズ`n`が与えられた二次固有値です。   [E. Jarlebring, The Spectrum of Delay-Differential Equations: Numerical Methods, Stability and Perturbation, PhD thesis, TU Braunschweig, Institut Computational Mathematics, Germany, 2008](https://nbn-resolving.org/urn:nbn:de:gbv:084-22041) および   [H. Fassbender, N. Mackey, D. S. Mackey and C. Schroeder, Structured Polynomial Eigenproblems Related to Time-Delay Systems, ETNA, 2008, vol 31, pp 306-330](http://etna.mcs.kent.edu/vol.31.2008/pp306-330.dir/)
  * `nlevp_native_loaded_string`: ネイティブNEP-PACK形式で表現されたNLEVPコレクションからのベンチマーク問題「pdde_stability」。   パラメータは(n,kappa,m)で、nはサイズで、NEPは有理項を持つSPMFで、係数行列はToeplitz行列のランク1の修正です。   [S. I. Solov"ev. Preconditioned iterative methods for a class of nonlinear eigenvalue problems. Linear Algebra Appl., 415 (2006), pp.210-229.](https://doi.org/10.1016/j.laa.2005.03.034)

# 例

```julia-repl
julia> nep=nep_gallery("dep0",100);
julia> norm(compute_Mlincomb(nep,1.0+1.0im,ones(size(nep,1))))
57.498446538064954
```

# 次のギャラリーも参照してください:

  * GalleryNLEVP
  * GalleryWaveguide

```
