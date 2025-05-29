与えられた[`ComponentContainer`](@ref)のようなコンポーネントのソース（例えば、[`PowerSystems.System`](@extref)）から、`ComponentSelector`はユーザー定義の選択基準に基づいて特定のサブセットを選択します。`ComponentSelector`は、そのコンポーネントのサブセットに名前を付けたり、グループに分割したりするためにも使用できます。同じ`ComponentSelector`を使用して、複数のコンポーネントソースに同じ選択基準を適用することもできます。`ComponentSelector`の主な使用ケースは、繰り返し可能なマルチシナリオのポストプロセッシング分析をサポートすることです（例えば、[`PowerAnalytics.jl`](https://nrel-sienna.github.io/PowerAnalytics.jl/stable/)を参照）。

正式には、`ComponentSelector`のインスタンスは、遅延、分割、名前付き、ソースに依存しない[`InfrastructureSystemsComponent`](@ref)のコレクションを表します。

# コアインターフェース

  * [`make_selector`](@ref): `ComponentSelector`の作成を処理するファクトリ関数。エンドユーザーは、コンストラクタを直接呼び出すのではなく、これを使用すべきです。
  * `get_groups`: `ComponentSelector`を構成するグループを取得します。これらはそれ自体が`ComponentSelector`として表されます。
  * `get_components`: グループ化の方法を無視して、`ComponentSelector`を構成するすべてのコンポーネントを取得します。コンポーネントは、特定のセレクタの`get_components`に表示される場合に限り、そのセレクタのグループの`get_components`に表示される必要があります。
  * [`get_name`](@ref): `ComponentSelector`の名前を取得します。すべての`ComponentSelector`には、ユーザーによって指定されたか自動的に作成されたかにかかわらず、名前があります。
  * [`rebuild_selector`](@ref): 既存の`ComponentSelector`から、いくつかの詳細（例えば、名前やグループ化の動作）を調整して新しい`ComponentSelector`を作成します。

# 利用可能性フィルタリング

コアインターフェースに加えて、最大1つのコンポーネントのみを参照できる`ComponentSelector`のサブタイプ用の`get_component`、および`get_available_component`、`get_available_components`、`get_available_groups`が提供されており、これらは`available`なしの対応する関数と同様に機能しますが、`get_available`がtrueであるコンポーネントのみを考慮します。

# `scope_limiter`フィルタリング

`get_component`、`get_components`、および`get_groups`の`ComponentSelector`メソッド、および対応する`_available_`バリアントは、オプションの最初の引数`scope_limiter::Union{Function, Nothing}`を取ります。ここに関数が渡されると、それは`ComponentSelector`の基準が評価される前に考慮されるコンポーネントを制限するためのフィルタ関数として使用されます。
