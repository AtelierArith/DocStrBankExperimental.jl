```
@either true ? "right" : Symbol("left")
@either if false
  "right"
else
  :left
end
```

Eitherを構築するために?演算子と単純なif-elseを再利用するシンプルなマクロ。
