```
DataLoader(data; [batchsize, buffer, collate, parallel, partial, rng, shuffle])
```

`data`のミニバッチを反復するオブジェクトであり、各ミニバッチには`batchsize`の観測が含まれます（最後のものは例外かもしれません）。

入力としては、単一のデータ配列、配列のタプル（または名前付きタプル）、または一般的に[`numobs`](@ref)および[`getobs`](@ref)メソッドを実装する任意の`data`オブジェクトを受け取ります。

各配列の最後の次元は観測次元であり、ミニバッチに分割される次元です。

元のデータはDataLoaderの`data`フィールドに保持されます。

# 引数

  * **`data`**: 反復するデータ。データ型は[`numobs`](@ref)および[`getobs`](@ref)によってサポートされている必要があります。
  * **`batchsize`**: 0未満の場合、個々の観測を反復します。それ以外の場合、各反復（最後のものを除く可能性があります）は`batchsize`の観測を含むミニバッチを生成します。デフォルトは`1`です。
  * **`buffer`**: `buffer=true`であり、`data`の型によってサポートされている場合、メモリ効率のためにバッファが割り当てられ再利用されます。サイズの不一致を避けるために`partial=false`を設定することをお勧めします。最後に、`getobs!`で使用する外部バッファを渡すことができます（`collate`および`batchsize`オプションに応じて、`getobs!(buffer, data, idxs)`または`getobs!(buffer[i], data, idx)`になる可能性があります）。デフォルトは`false`です。
  * **`collate`**: バッチ処理の動作を定義します。デフォルトは`nothing`です。

      * `nothing`の場合、バッチは`getobs(data, indices)`です。
      * `false`の場合、各バッチは`[getobs(data, i) for i in indices]`です。
      * `true`の場合、バッチ内の観測のベクトルに`MLUtils.batch`を適用し、最後の次元で配列を再帰的に集約します。詳細や例については[`MLUtils.batch`](@ref)を参照してください。
      * カスタム関数の場合、`MLUtils.batch`の代わりに使用されます。観測のベクトルを入力として受け取る必要があります。
  * **`parallel`**: ワーカースレッドを使用してデータを並行してロードするかどうか。利用可能なスレッドの数によってデータのロードが大幅に高速化されます。複数のスレッドでJuliaを起動する必要があります。利用可能なスレッドの数を確認するには`Threads.nthreads()`をチェックしてください。**`parallel = true`を渡すと順序保証が破られます**。デフォルトは`false`です。
  * **`partial`**: この引数は`batchsize > 0`のときのみ使用されます。`partial=false`で観測の数がバッチサイズで割り切れない場合、最後のミニバッチはドロップされます。デフォルトは`true`です。
  * **`rng`**: 擬似乱数生成器。デフォルトは`Random.default_rng()`です。
  * **`shuffle`**: 反復する前に観測をシャッフルするかどうか。`shuffleobs(data)`でデータコンテナをラップするのとは異なり、`shuffle=true`は、`eachobs`を反復するたびに観測が新たにシャッフルされることを保証します。デフォルトは`false`です。

# 例

```jldoctest
julia> Xtrain = rand(10, 100);

julia> array_loader = DataLoader(Xtrain, batchsize=2);

julia> for x in array_loader
         @assert size(x) == (10, 2)
         # xを使って何かをする、50回
       end

julia> array_loader.data === Xtrain
true

julia> tuple_loader = DataLoader((Xtrain,), batchsize=2);  # 同様ですが、1要素のタプルを生成します

julia> for x in tuple_loader
         @assert x isa Tuple{Matrix}
         @assert size(x[1]) == (10, 2)
       end

julia> Ytrain = rand('a':'z', 100);  # 2要素の名前付きタプルを生成するDataLoaderを作成します

julia> train_loader = DataLoader((data=Xtrain, label=Ytrain), batchsize=5, shuffle=true);

julia> for epoch in 1:100
         for (x, y) in train_loader  # タプルの分解を介してアクセス
           @assert size(x) == (10, 5)
           @assert size(y) == (5,)
           # loss += f(x, y) # など、100 * 20回実行
         end
       end

julia> first(train_loader).label isa Vector{Char}  # プロパティ名を介してアクセス
true

julia> first(train_loader).label == Ytrain[1:5]  # shuffle=trueのため
false

julia> foreach(println∘summary, DataLoader(rand(Int8, 10, 64), batchsize=30))  # partial=falseは最後を省略します
10×30 Matrix{Int8}
10×30 Matrix{Int8}
10×4 Matrix{Int8}

julia> collate_fn(batch) = join(batch);

julia> first(DataLoader(["a", "b", "c", "d"], batchsize=2, collate=collate_fn))
"ab"
```
