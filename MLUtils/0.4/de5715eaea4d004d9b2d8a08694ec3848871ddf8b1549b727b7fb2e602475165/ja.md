```
BatchView(data, batchsize; partial=true, collate=nothing)
BatchView(data; batchsize=1, partial=true, collate=nothing)
```

与えられた `data` のビューを作成し、それをバッチのベクトルとして表現します。各バッチには等しい数の観測が含まれます。バッチサイズは `batchsize` パラメータを使用して指定できます。データセットのサイズが指定された `batchsize` で割り切れない場合、残りの観測は `partial=false` の場合は無視されます。代わりに `partial=true` の場合、最後のバッチサイズは少し小さくなる可能性があります。

イテレータとして使用される場合、オブジェクトはデータセットを一度繰り返し、効果的にエポックを示します。

データアクセスは、イテレーションまたはインデックス付けが行われるまで遅延されます。観測を取得するために、データオブジェクトに対して [`getobs`](@ref MLUtils.getobs) 関数が呼び出されます。

`BatchView` が特定のデータ構造で機能するためには、与えられた変数 `data` の型がデータコンテナインターフェースを実装している必要があります。詳細については [`ObsView`](@ref) を参照してください。

# 引数

  * **`data`** : データセットを説明するオブジェクト。 [`getobs`](@ref) と [`numobs`](@ref) を実装している限り、任意の型で構いません（詳細についてはさらに情報を参照してください）。
  * **`batchsize`** : 各バッチのバッチサイズ。各バッチが含むべき観測の数です（最後のバッチは例外かもしれません）。
  * **`partial`** : `partial=false` の場合、観測の数がバッチサイズで割り切れないと、最後のミニバッチはドロップされます。
  * **`collate`**: バッチ処理の動作を定義します。

      * `nothing`（デフォルト）の場合、バッチは `getobs(data, indices)` です。
      * `false` の場合、各バッチは `[getobs(data, i) for i in indices]` です。
      * `true` の場合、バッチ内の観測のベクトルに MLUtils を適用し、最後の次元で配列を再帰的に結合します。詳細と例については [`MLUtils.batch`](@ref) を参照してください。
      * カスタム関数の場合、`MLUtils.batch` の代わりに使用されます。観測のベクトルを入力として受け取る必要があります。

[`DataLoader`](@ref) も参照してください。

# 例

```jldoctest
julia> using MLUtils

julia> X, Y = MLUtils.load_iris();

julia> A = BatchView(X, batchsize=30);

julia> @assert eltype(A) <: Matrix{Float64}

julia> @assert length(A) == 5 # アイリスには150の観測があります

julia> @assert size(A[1]) == (4,30) # アイリスには4つの特徴があります

julia> for x in BatchView(X, batchsize=30)
           # 30の観測からなる5つのバッチ
           @assert size(x) == (4, 30)
           @assert numobs(x) === 30
       end

julia> for (x, y) in BatchView((X, Y), batchsize=20, partial=true)
           # 20の観測からなる7つのバッチ + 10の観測からなる1つのバッチ
           @assert typeof(x) <: Matrix{Float64}
           @assert typeof(y) <: Vector{String}
       end

julia> for batch in BatchView((X, Y), batchsize=20, partial=false, collate=false)
           # 20の観測からなる7つのバッチ
           @assert length(batch) == 20
           x1, y1 = batch[1]
       end

julia> function collate_fn(batch)
           # 観測をカスタムバッチに結合する
           return hcat([x[1] for x in batch]...), join([x[2] for x in batch])
        end;

julia> for (x, y) in BatchView((rand(10, 4), ["a", "b", "c", "d"]), batchsize=2, collate=collate_fn)
           @assert size(x) == (10, 2)
           @assert y isa String
       end
```
