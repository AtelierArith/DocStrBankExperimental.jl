```
simulate(
    pool::AbstractArray{Pseudoread},
    refseq::BioSequence,
    subcon::AbstractArray{Variation{S,T}};
    reverse_order::Union{Bool,Nothing}=nothing,
    overlap_min::Int64=0,
    overlap_max::Int64=500,
) where {S,T} -> Union{Haplotype{S,T},Nothing}
```

新しいセットの[`Pseudoread`](@ref)sを、最大尤度シミュレーションを使用してスプライスされた実際のリードの`pool`に基づいて作成します。

# 引数

  * `pool::AbstractArray{Pseudoread}`: 新しいシミュレートされたリードの部品として使用される（おそらく）実際のシーケンシングリードのセット。
  * `refseq::BioSequence`: `pool`および`subcon`内のすべてのシーケンスが整列された参照。
  * `subcon::AbstractArray{Variation{S,T}}`: `pool`に存在し、実際のものである（すなわち、シーケンシングエラーによるものでない）ことが知られているサブコンセンサス`Variation`。

# オプション

  * `reverse_order::Union{Bool,Nothing}=nothing`: スプライシングを参照シーケンスの先頭または末尾から開始するかどうか。空白のままにすると、ランダムに決定されます。
  * `overlap_min::Int64=0`: `pool`からのリードがスプライスされるために重複する必要がある量。負の値を指定すると、リードがこの量だけ離れている必要があることを示します。 -`overlap_max::Int64=500`: プールからのリードが破棄される前に重複できる量。`overlap_min`と同様に、負の値を指定できます。

# 戻り値

シミュレートされたリードを表す`Haplotype{S,T}`、またはシミュレーションが行き詰まった場合は`nothing`。

# 拡張ヘルプ

シミュレーション手順は、`subcon`からの最初の（`reverse_order`がfalseの場合は最後の）バリアントを含む`pool`からリードを選択することによって機能します。手順は、選択されたリードがその位置をもはや持たなくなるまで、`subcon`内のすべての位置を昇順（または`reverse_order == true`の場合は降順）で調べます。シミュレーションは、その後、ランダムに`pool`から次の`subcon`の位置を含むリードを選択し、かつ*前のリードと同じ`subcon`内のすべての位置で一致するバリエーションを持ち*、重複要件を満たす必要があります。これらの2つのリードは、`subcon`内のサイト以外のサイトで異なる場合があります：適切なバリアントコールがすでに実行されており、これらのサイトの変動はシーケンシングエラーによるものであると仮定されます。手順は、シミュレーションが`subcon`のすべての位置をシミュレートするか、行き詰まりに達してすべての要件に一致するリードを見つけられなくなるまで、`pool`からの新しいリードごとに繰り返されます。
