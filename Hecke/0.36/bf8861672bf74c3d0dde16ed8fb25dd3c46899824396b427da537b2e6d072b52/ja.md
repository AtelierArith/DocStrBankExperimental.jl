```
enumerate_definite_genus(known::Vector{ZZLat}, algorithm::Symbol = :default) -> Vector{ZZLat}, QQFieldElem
enumerate_definite_genus(L::ZZLat, algorithm::Symbol = :default) -> Vector{ZZLat}
enumerate_definite_genus(G::ZZGenus, algorithm::Symbol = :default) -> Vector{ZZLat}
```

与えられた定義格子の属の中で、ランクが少なくとも `3` の整数定義格子を列挙するために、クネザーの隣接アルゴリズムを使用します。

出力は、与えられた属における等長クラスを表す格子のリストで構成されます。

最初の引数には、属の記号 $G$ を直接指定するか、属 $G$ にある格子 $L$ を指定することができます。そうでない場合は、既知の格子のリスト $G$ を与えて不完全な列挙を続けることができます（この場合、格子は同じスピノル属にあると仮定されます）。

2 番目の引数は、列挙に使用するアルゴリズムを選択するためのものです。現在、2 つのアルゴリズムをサポートしています：

  * `:random` は、ランダムな同次直線から隣接を構築することによって新しい等長クラスを見つけます；
  * `:orbit` は、隣接を構築する前に同次直線の軌道を計算します。

`algorithm = :default` の場合、関数は列挙される属のランクと行列式に応じて最も適切なアルゴリズムを選択します。

追加のオプション引数が可能です：

  * `rand_neigh::Int` (デフォルト = `10`) -> ランダム列挙の場合、各イテレーションで計算されるランダムな隣接の数；
  * `invariant_function::Function` (デフォルト = `default_invariant_function`) -> 不必要な等長テストを避けるために等長不変量を計算する関数；
  * `save_partial::Bool` (デフォルト = `false`) -> 新しい等長クラスを逐次保存したいかどうか（例えば、大きな属の場合）；
  * `save_path::String` (デフォルト = `nothing`) -> `save_partial` が true の場合に新しい格子を保存するフォルダへのパス；
  * `use_mass::Bool` (デフォルト = `true`) -> 終了条件として質量公式を使用するかどうか；
  * `stop_after::IntExt` (デフォルト = `inf`) -> 新しい等長クラスが見つからないまま指定された無駄なイテレーションの数に達した場合にアルゴリズムが停止；
  * `max::IntExt` (デフォルト = `inf`) -> `max` の新しい等長クラスを見つけた後にアルゴリズムが停止。

入力として `known` 格子のリストを与えた場合、出力リストには `known` のコピーと計算された新しい格子が含まれます。関数の追加出力は、欠けている（スピノル）属の質量の部分を示す有理数です。質量が使用されていない場合（`use_mass = false`）、これは `0` に設定されます。さらに、他に 2 つの追加オプション引数があります：

  * `distinct::Bool` (デフォルト = `false`) -> `known` の格子が対になって非等長であることが知られているかどうか；
  * `missing_mass::QQFieldElem` (デフォルト = `nothing`) -> `use_mass` と `distinct` が true で、`known` の部分質量が知られている場合、欠けている質量の部分を示します；

`distinct == false` の場合、関数は最初に `known` のすべての格子を比較して、各等長クラスを代表する格子を 1 つだけ保持します。

`save_partial == true` の場合、格子は `.txt` ファイルにコンパクトに保存されます。保存は、格子のランク、グラム行列の半分（格子を独立したオブジェクトとして再構築するのに十分）および格子の等長群の順序を記憶します。

`default_invariant_function` は現在次のものを計算します：

  * 与えられた格子の最短ベクトルの絶対長さ（[`minimum`](@ref) としても知られています）；
  * 与えられた格子の根部分格子の分解からなるタプルの順序付きリスト（[`root_lattice_recognition`](@ref) を参照）；
  * 与えられた格子のキス数、これは最短長のベクトルの数に比例します；
  * 与えられた格子の等長群の順序。

```
