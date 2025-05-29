```
abstract type Algorithm{M <: Manifold}
```

すべての GeometryOps アルゴリズムのための抽象スーパタイプです。これらは特定の [`Operation`](@ref) を実行する方法を定義します。

アルゴリズムは、1つまたは複数の [`Manifold`](@ref) に関連付けられる場合があります。マニフォールドをフィールドとして持つか、静的パラメータとして持つことができます（例: `struct GEOS <: Algorithm{Planar}`）。

## インターフェース

すべての `Algorithm` は以下のメソッドを実装しなければなりません：

  * `rebuild(alg, manifold::Manifold)` 新しいマニフォールドを第二引数として渡してアルゴリズム `alg` を再構築します。マニフォールドがそのアルゴリズムと互換性がない場合、[`WrongManifoldException`](@ref) をスローしてエラーになる可能性があります。
  * `manifold(alg::Algorithm)` アルゴリズムに関連付けられたマニフォールドを返します。
  * `best_manifold(alg::Algorithm, input)`: 他のコンテキストがない場合、そのアルゴリズムに最適なマニフォールドを返します。警告: これは将来変更される可能性があり、安定していません！

実際の実装は、その特定の [`Operation`](@ref) の実装に委ねられています。

## 注目すべきサブタイプ

  * [`AutoAlgorithm`](@ref): 受け取った [`Operation`](@ref) に対して、入力データに最適なアルゴリズムを自動的に選択するよう指示します。
  * [`ManifoldIndependentAlgorithm`](@ref): 任意のマニフォールドで動作するアルゴリズムのための抽象スーパタイプです。`ManifoldIndependentAlgorithm` のアルゴリズムにはマニフォールドが保存され、`manifold(alg)` を介してアクセスされる必要があります。
  * [`SingleManifoldAlgorithm`](@ref): 単一のマニフォールドでのみ動作するアルゴリズムのための抽象スーパタイプです。これはその型パラメータで指定されます。`SingleManifoldAlgorithm{Planar}` は特別なケースで、情報を含まないためマニフォールドを保存する必要はありません。他のすべての `SingleManifoldAlgorithm` は情報を含むため、マニフォールドを保存する必要があります。
  * [`NoAlgorithm`](@ref): アルゴリズムが使用されないことを示す型で、実質的には `nothing` と同等です。
