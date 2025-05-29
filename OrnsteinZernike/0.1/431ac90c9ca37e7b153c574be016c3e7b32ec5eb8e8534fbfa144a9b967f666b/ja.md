```
FourierIteration <: Method
```

フーリエ空間での再帰的反復によってシステムを解決します。本質的に、アルゴリズムは次のようになります：

1. 初期の γ(r) を推測する
2. 閉包関係を使用して c(r) を見つける
3. フーリエ変換を行って ĉ(k) を得る
4. k空間で OZ-eq を使用して γ(k) を見つける
5. 逆フーリエ変換を用いて γ(r) を計算する
6. 前の値と比較し、収束していない場合は 2 に戻る。

オプションとして、ステップ 2 で c(r) の新しい反復と前の反復を混合するために混合ルールが使用されます。

引数：

  * `M::Int`: 解を離散化する点の数
  * `dr::Float64`: 実空間でのグリッド間隔
  * `mixing_parameter::Float64`: 反復混合のための混合パラメータ。1 の値は混合なし。0 と 1 の間でなければならない。
  * `max_iterations::Int64`: 最大反復回数
  * `tolerance::Float64`: 達成すべき許容誤差
  * `verbose::Bool`: 収束情報を印刷するかどうか

デフォルト: `FourierIteration(; mixing_parameter=0.5, max_iterations=10^5, tolerance=10^-6, verbose=true, M=1000, dr=10.0/M)`
