与えられたシンドロームをデコードする関数

# 引数

  * `decoder`: ビットフリップデコーダの設定
  * `syndrome`: 入力として取られるシンドローム
  * `errors`: この関数が操作する事前定義されたエラー配列

# 例

```jldoctest
julia> H = LDPCDecoders.parity_check_matrix(1000, 10, 9);

julia> decoder = BitFlipDecoder(H, 0.01, 100);

julia> error = rand(1000) .< 0.01;

julia> syndrome = (H * error) .% 2;

julia> guess, success = decode!(decoder, syndrome);

julia> error == guess
true
```
