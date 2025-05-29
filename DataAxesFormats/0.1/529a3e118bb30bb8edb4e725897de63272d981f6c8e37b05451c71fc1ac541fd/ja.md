`DataAxesFormats`パッケージは、いくつかの軸に沿って配置された1Dおよび2Dデータにアクセスするための均一な汎用インターフェースを提供します。これは、[AnnData](https://pypi.org/project/anndata/)機能の必要な一般化です。主な特徴は次のとおりです。

  * データモデル[`StorageTypes`](@ref)には、(1) 名前付きエントリを持ついくつかの軸、(2) 単一の軸でインデックスされたベクトルデータ、(3) 一対の軸でインデックスされた行列データ、(4) いかなる軸にも結びついていないスカラーデータが含まれます。
  * 2Dデータ[`MatrixLayouts`](@ref)に対する明示的な制御（行優先または列優先）を提供し、パフォーマンスにとって重要な密な行列と疎な行列の両方をサポートします。
  * すぐに使用できる状態で、データをメモリに保存することを許可します（[`MemoryDaf`](@ref)を使用）、[HDF5](https://www.hdfgroup.org/solutions/hdf5/)ファイル内に直接保存すること（[`H5df`](@ref)を使用）、またはディレクトリ内の単純なファイルのコレクションとして保存すること（[`FilesDaf`](@ref)を使用）を行い、計算パイプラインの自動化に`make`のようなツールともうまく連携します。
  * 非`Daf`ツールとの相互運用性のために、[`AnnDataFormat`](@ref)へのインポートおよびエクスポートを行います。
  * 大規模データセットの効率的な処理を可能にするために、メモリマッピングに焦点を当てた実装（理論的には、システムのメモリよりも大きいデータセット）。特に、データセットを開くだけで、サイズに関係なく（ほぼ）高速な操作です。
  * 追加のストレージ[`Formats`](@ref)を実装するための明確に定義されたインターフェース。
  * データセットの[`Chains`](@ref)を作成し、複数の計算パイプライン間で共通データのゼロコピー再利用を可能にします。
  * 一つまたは複数の軸に沿って複数のデータセットを単一のデータセットに[`Concat`](@ref)します。
  * データにアクセスするための[`Query`](@ref)言語を提供し、スライス、集約、フィルタリングなどの機能を提供し、これらのクエリに基づいて[`Views`](@ref)および[`Copies`](@ref)を作成します。
  * 明示的な[`Contracts`](@ref)を持つ自己文書化された[`Computations`](@ref)があり、入力と出力を説明し強制し、異なる形式のデータに計算を適用するための[`Adapters`](@ref)があります。

!!! note
    トップレベルの`DataAxesFormats`モジュールは、サブモジュールからすべて（ほとんど）を再エクスポートするため、`using DataAxesFormats`（または`import DataAxesFormats: MemoryDaf`）を使用して、エクスポートされたシンボルに直接アクセスできます。これにより、`DataAxesFormats.MemoryFormat.MemoryDaf`のような修飾名をインポートまたは使用する必要がなくなります。


`Daf`データセットのタイプ階層は次のようになります：

```
DafReader (abstract type)
├─ DafReadOnly (abstract type)
│  ├─ DafReadOnlyWrapper (created by read_only)
│  ├─ DafView (created by viewer)
│  └─ DafChainReader (created by chain_reader)
└─ DafWriter (abstract type)
   ├─ DafChainWriter (created by chain_writer)
   ├─ MemoryDaf
   ├─ FilesDaf
   └─ H5df
```
