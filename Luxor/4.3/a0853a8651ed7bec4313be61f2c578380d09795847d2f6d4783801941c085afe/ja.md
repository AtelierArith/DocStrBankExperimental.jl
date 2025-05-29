```
polymorph(pgon1::Array{Vector{Point}}, pgon2::Array{Vector{Point}}, k;
    samples = 100,
    easingfunction = easingflat,
    kludge = true
    closed = true)
```

「morph」とは、あるものから別のものに徐々に変化することを意味します。この関数は、一つの多角形を別の多角形に変換します。

それは多角形の配列 `[p_1, p_2, p_3, ... ]` を返します。ここで、各多角形 `p_n` は、`pgon1[1...n]` と `pgon2[1...n]` の対応する形の間の中間的な形状であり、`k` において、`0.0 < k < 1.0` の範囲にあります。もし `k ≈ 0.0` であれば、`pgon1[1...n]` が返され、もし `k ≈ 1.0` であれば、`pgon2[1...n]` が返されます。

`pgon1` と `pgon2` は、各々が三つ以上の点を持つ単純な多角形であるか、または一つ以上の多角形の形状の配列（例えば `pathtopoly()` によって作成されたもの）であることができます。例えば、`pgon1` は二つの多角形の形状、すなわち、四角形とその中にある三角形の穴から構成されるかもしれません；`pgon2` は、四角形の穴を持つ三角形の形状かもしれません。

両方の引数が同じ数の多角形の形状を持つことは理にかなっています。一方が他方よりも多い場合、変形する際にいくつかの形状が失われることになります。しかし、示唆的に名付けられた `kludge` キーワード引数は、（デフォルトで）true に設定されている場合、これを補うように試みます。

デフォルトでは、`easingfunction = easingflat` であるため、中間ステップは線形です。別のイージング関数を使用すると、中間ステップは `k` におけるイージング関数の値によって決まります。

`polysample()` は多角形を開いているか閉じているかとして扱うことができるため（異なる結果を伴う）、ここでサンプリングがどのように行われるかを `closed=` キーワードで指定できます：

  * closed = true -> 多角形は閉じたものとしてサンプリングされる
  * closed = false -> 多角形は開いたものとしてサンプリングされる
  * closed = (true, false) -> 最初の多角形は閉じたものとしてサンプリングされ、二番目は開いたものとしてサンプリングされる

この関数は非常に効率的ではありません。なぜなら、多角形をコピーして再サンプリングするからです。

TODO : 実験的であり、確実に改善できるでしょう。

# 拡張ヘルプ

### 例

この小さな四角形と大きな八角形の間の単純なモーフィングは、イージング関数 `easeinoutinversequad` によって制御されており、遷移の中間で減速します。

返される多角形配列の最初の形状のみが必要です。

```julia
pgon1 = ngon(O, 30, 4, 0, vertices = true)
pgon2 = ngon(O, 220, 8, 0, vertices = true)
for i in 0:0.1:1.0
    poly(first(polymorph(pgon1, pgon2, i,
            easingfunction = easeinoutinversequad)),
        action = :stroke,
        close = true)
end
```

次の例では、最初の形状 - 四角い穴のある円 - と二番目の形状、円形の穴のある四角形の間でモーフィングします。

```julia
ngon(O - (250, 0), 30, 50, 0, :path)
newsubpath()
ngon(O - (250, 0), 10, 4, 0, reversepath = true, :path)
pg1 = pathtopoly()

newpath()
ngon(O + (250, 0), 30, 4, 0, :path)
newsubpath()
ngon(O + (250, 0), 10, 50, 0, reversepath = true, :path)
pg2 = pathtopoly()

for i in reverse(0.0:0.1:1.0)
    randomhue()
    newpath()
    # 正しい「穴」の性質を保持するために :path の後に fillpath() を使用
    poly.(polymorph(pg1, pg2, i), :path, close = true)
    fillpath()
end
```
