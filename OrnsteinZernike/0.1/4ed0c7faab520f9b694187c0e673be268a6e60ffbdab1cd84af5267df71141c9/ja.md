```
NgIteration <: Method
```

フーリエ空間での再帰的反復によってシステムを解決し、Ng加速法を使用します。基本的に、アルゴリズムは次のようになります：

1. 初期のγ(r)を推測する
2. 閉包関係を使用してc(r)を見つける
3. フーリエ変換を行いĉ(k)を得る
4. k空間でOZ方程式を使用してγ(k)を見つける
5. 逆フーリエ変換を用いてγ(r)を計算する
6. Ngの方法を使用してγの次の推測を提供する
7. 前の値と比較し、収束していない場合は2に戻る。

引数：

  * `M::Int`: 解を離散化する点の数
  * `dr::Float64`: 実空間でのグリッド間隔
  * `N_stages::Int`: ステップ6で考慮する前の値の数。より高い数はより速い収束をもたらすはずですが、各反復あたりの計算時間が増加します。
  * `max_iterations::Int64`: 最大反復回数
  * `tolerance::Float64`: 達成すべき許容誤差
  * `verbose::Bool`: 収束情報を印刷するかどうか

デフォルト: `NgIteration(; N_stages=3, max_iterations=10^3, tolerance=10^-6, verbose=true, M=1000, dr=10.0/M)`

参考文献: Ng, K. C. (1974). Hypernetted chain solutions for the classical one‐component plasma up to Γ= 7000. The Journal of Chemical Physics, 61(7), 2680-2689.
