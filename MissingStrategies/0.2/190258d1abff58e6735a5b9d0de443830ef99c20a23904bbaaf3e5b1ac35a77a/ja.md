@handlemissings_typed(fun, ...)

[`handlemissings`](@ref)を、eltypeがmissingを受け入れない元のメソッドに合わせたデフォルトで呼び出します：

  * [`@handlemissings_stub`](@ref)と同様にメソッドをディスパッチします
  * 新しい関数の引数の型を指定する必要があります。`Any`を使用できます。デフォルトメソッド（`MissingStrategy`引数なし）が作成され、PassMissingメソッドにフォワードされます。したがって、元のメソッドが上書きされないように、引数の型が元のメソッドと異なることを確認してください。
  * PassMissingメソッドは、各要素が対応するnonmissing型に変換されたブロードキャストで元のメソッドを呼び出します（[`mgen.passmissing_convert`](@ref)）。
  * SkipMissingメソッドは、元の関数を呼び出す前にskipmissingオブジェクトを収集します（[`mgen.handlemissing_collect_skip`](@ref)）。

引数：[`handlemissings`](@ref)を参照してください    

# デフォルトMissingStrategyに関する注意

引数の位置でデフォルトMissingStrategyを定義することは、直感的でない動作をする場合があります。

```julia
f2(x::AbstractArray{<:Real},optarg=1:3) = x
@handlemissings_typed(f2(x::AbstractArray{<:Real},optarg=1:3)=0,1,2,Any)
# f2(x,ms::MissingStrategy=PassMissing(),optarg=1:3) # 生成された
# f2([1.0,missing], 2:4) # メソッドが定義されていない -> 引数の順序を再考
```

上記のケースでPassMissingバリアントを呼び出すには、単一の引数を持つメソッドと二つの引数を持つメソッドのために`@handle_missing_typed`を別々に呼び出し、二つ目のケースではデフォルトmissing戦略を二つ目の引数の後ろに置く必要があります。

```julia
f3(x::AbstractArray{<:Real},optarg=1:3) = x
@handlemissings_typed(f3(x::AbstractArray{<:Real})=0,1,2,Any)
@handlemissings_typed(f3(x::AbstractArray{<:Real}, optarg)=0,1,3,Any)
ismissing(f3([1.0,missing], 2:4))
```
