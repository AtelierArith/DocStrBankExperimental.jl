The TopHatFilter{T <: AbstractFloat} 構造体は、スペクトルデータに適用されると、定常的および緩やかに変化する信号（連続体のような）を抑制し、特性ピークのような急速に変化する信号に対して線形信号を保持する特性を持つゼロサム対称二次導関数のようなフィルタを表します。

参照：

  * F. H. Schamber Proc Symposium of "X-ray Fluorscence Analysis on Environmental Samples" Chapel Hill 1976 T Dzubay Ed.
  * P. Statham Anal Chem 49 no 14 Dec 1977

TopHatFilter 構造体は、スペクトルデータにトップハットフィルタを適用する際のメモリと CPU の使用を最適化します。

トップハットフィルタを実装する最も簡単な方法は、行列 F として実装することです。行はフィルタを表します。フィルタとデータベクトルの積はフィルタリングされたスペクトルです。フィルタとデータから構築された対角行列との積のフィルタの転置との積は、フィルタリングされたデータの共分散です。スペクトルデータから構築された対角行列は、スペクトルデータに関連する共分散行列です。なぜなら、スペクトルデータのチャネルは独立しているため（したがって行列は対角行列です）、その大きさは各チャネルのカウントに等しいからです。スペクトルデータは名目上ポアソン分布に従い、大数の極限において、ポアソンランダム変数の分散はその数自体に等しいからです（σ=sqrt(N) => Var = N）。

メモリとコードの最適化に関する注意：フィルタ行列はバンド対角です。おおよそ、2.5% の要素が非ゼロです。これは BandedMatrix 型の使用を示唆しています。最もコストのかかる操作は、フィルタリングされたデータの共分散行列 F⋅D⋅Fᵀ を計算することです。D は対角行列であるため、F⋅D⋅Fᵀ の各要素を計算することは、単一の変数に対する合計に簡略化されます。さらに、加重最小二乗フィットは完全な F⋅D⋅Fᵀ を必要とせず、diag(F⋅D⋅Fᵀ) だけが必要です。しかし、D が完全に対角であるため、独自のバンド行列型を実装することでより良い結果が得られることがわかります。行列積 F⋅D⋅Fᵀ は単一の変数に対する合計に簡略化されます。積 F⋅d と F⋅D⋅Fᵀ は、要素ごとの乗算と合計として容易に実装できます。したがって、フィルタをオフセットと行フィルタとして保存することは、メモリと CPU の使用の両方において効率的です。
