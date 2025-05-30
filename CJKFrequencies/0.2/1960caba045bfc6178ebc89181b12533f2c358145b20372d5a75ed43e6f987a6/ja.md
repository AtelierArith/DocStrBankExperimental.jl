```
SimplifiedJunDa()
```

現代中国語の文字頻度 [データセット](https://lingua.mtsu.edu/chinese-computing/) は、Jun Da によって編纂されたもので、簡体字の単一文字の単語のみを含みます。

現在、現代中国語のデータセットのみが取得されますが、将来的には他のリストもオプションとして提供される可能性があります。

## 例

```julia-repl
julia> charfreq(SimplifiedJunDa())
DataStructures.Accumulator{String,Int64} with 9932 entries:
  "蜷… => 837
  "哇… => 4055
  "湓… => 62
  "滴… => 8104
  "堞… => 74
  "狭… => 6901
  "尚… => 38376
  "懈… => 2893
  ⋮   => ⋮
```

## ライセンス/著作権

元の著者は文字頻度リストに対する完全な著作権を保持していますが、リストは研究および教育/学習目的のみに提供されており、著者の許可なしに商業利用はできません。完全な免責事項と著作権通知は [こちら](https://lingua.mtsu.edu/chinese-computing/copyright.html) でご覧ください。
