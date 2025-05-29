```
struct VarInfo{Tmeta,Tlogp} <: AbstractVarInfo
    metadata::Tmeta
    logp::Base.RefValue{Tlogp}
    num_produce::Base.RefValue{Int}
end
```

ある種のメタデータに対する軽量ラッパーです。

メタデータの型は、いくつかのオプションのいずれかである可能性があります。`Metadata`または`VarNamedVector`であるか、*または*、シンボルを`Metadata`または`VarNamedVector`インスタンスにマッピングする`NamedTuple`である可能性があります。ここで、*シンボル*はJuliaの変数を指し、チルダ文の左側に現れる1つ以上の`VarName`で構成される場合があります。例えば、`x[1]`と`x[2]`はどちらも同じシンボル`x`を持っています。

これらのVarInfoの形式に対していくつかの型エイリアスが提供されています：

  * `VarInfo{<:Metadata}`は`UntypedVarInfo`です
  * `VarInfo{<:VarNamedVector}`は`UntypedVectorVarInfo`です
  * `VarInfo{<:NamedTuple}`は`NTVarInfo`です

NamedTuple形式、すなわち`NTVarInfo`は、モデル評価の型安定性を維持するのに役立ちます。ただし、NamedTupleの要素型はその型自体には含まれていないため、型システムを使用してNamedTupleの要素が`Metadata`または`VarNamedVector`であるかどうかを判断する方法はありません。

NTVarInfoについては、モデル評価中に各シンボルが少なくとも1回は訪問されることをユーザーが保証する責任があります。これは、確率的分岐に関係なくです。
