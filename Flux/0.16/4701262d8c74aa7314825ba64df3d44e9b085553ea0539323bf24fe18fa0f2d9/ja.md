```
Recurrence(cell)
```

再帰的な `cell`（例えば、[`RNNCell`](@ref)、[`LSTMCell`](@ref)、または[`GRUCell`](@ref)）から全体のシーケンスを処理する再帰層を作成します。これは、[`RNN`](@ref)、[`LSTM`](@ref)、および[`GRU`](@ref)がシーケンスを処理する方法に似ています。

`cell` は、入力 `x` と隠れ状態 `state` を受け取り、新しい隠れ状態 `state'` を返す呼び出し可能なオブジェクトである必要があります。また、`cell` は初期隠れ状態を返す `initialstates` メソッドを実装する必要があります。`cell` の出力は次のように考えられます：

1. `state` がタプルの場合、`state` タプルの最初の要素（例えば、LSTMの場合は `(h, c)`）。
2. `state` がタプルでない場合、RNNおよびGRUの場合の配列 `h` など、`state` 自体。

# フォワード

```
rnn(x, [state])
```

入力 `x` は、サイズ `in x len` または `in x len x batch_size` の配列である必要があります。ここで、`in` はセルの入力次元、`len` はシーケンスの長さ、`batch_size` はバッチサイズです。`state` は再帰セルの有効な状態である必要があります。提供されていない場合は、`Flux.initialstates(cell)` を呼び出すことで取得されます。

出力は、サイズ `out x len x batch_size` の配列であり、ここで `out` はセルの出力次元です。

実行される操作は、次のコードと意味的に同等です：

```julia
out_from_state(state) = state
out_from_state(state::Tuple) = state[1]

state = Flux.initialstates(cell)
out = []
for x_t in eachslice(x, dims = 2)
  state = cell(x_t, state)
  out = [out..., out_from_state(state)]
end
stack(out, dims = 2)
```

# 例

```jldoctest
julia> rnn = Recurrence(RNNCell(2 => 3))
Recurrence(
  RNNCell(2 => 3, tanh),                # 18 パラメータ
)                   # 合計: 3 配列、18 パラメータ、232 バイト。

julia> x = rand(Float32, 2, 3, 4); # in x len x batch_size

julia> y = rnn(x); # out x len x batch_size
```
