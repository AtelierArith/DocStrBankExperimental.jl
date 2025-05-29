```
domoves(b::Board, moves::Vararg{Move})
domoves(b::Board, moves::Vararg{String}; movelist::MoveList = MoveList(200))

開始ボード `b` から一連の手を指すことによって得られるボードを返します。

入力ボード `b` は変更されません。

提供された手が文字列の場合、この関数はまず手をUCI手として解析し、UCI手の解析が失敗した場合はSAN手として解析しようとします。

すべての手が合法であることを確認するのは呼び出し元の責任です。単純な手が違法である場合、その結果は未定義です。手の文字列が明確な合法的な手として解析できない場合、関数は例外をスローします。

`move::Vararg{String}` の場合、`movefromsan` が呼び出されます。これは、不要なアロケーションによる時間/スペースの節約のために、事前に割り当てられた `MoveList` を供給することができます。提供された場合、`movelist` パラメータは `movefromsan` に渡されます。`movelist` が十分な容量を持っていることを確認するのは呼び出し元の責任です。

このバージョンの破壊的なバージョンもあり、`domoves!` という名前です。

# 例

```

julia-repl julia> b = startboard();

julia> domoves(b, "d4", "Nf6", "c4", "e6", "Nc3", "Bb4") Board (rnbqk2r/pppp1ppp/4pn2/8/1bPP4/2N5/PP2PPPP/R1BQKBNR w KQkq -):  r  n  b  q  k  -  -  r  p  p  p  p  -  p  p  p

  *   *   *   * p  n  -  -
  *   *   *   *   *   *   *   *
  * b  P  P  -  -  -  -
  *   * N  -  -  -  -  -

P  P  -  -  P  P  P  P  R  -  B  Q  K  B  N  R

julia> movelist = MoveList(200) 0-element MoveList

julia> domoves(b, "d4", "Nf6", "c4", "e6", "Nc3", "Bb4"; movelist=movelist) Board (rnbqk2r/pppp1ppp/4pn2/8/1bPP4/2N5/PP2PPPP/R1BQKBNR w KQkq -):  r  n  b  q  k  -  -  r  p  p  p  p  -  p  p  p

  *   *   *   * p  n  -  -
  *   *   *   *   *   *   *   *
  * b  P  P  -  -  -  -
  *   * N  -  -  -  -  -

P  P  -  -  P  P  P  P  R  -  B  Q  K  B  N  R

julia> domoves(b, "d4", "Nf6", "c5") ERROR: "Illegal or ambiguous move: c5" ```
