```
cut2 = convert_cut(cut::Cut, icomp::Integer)
```

`cut`のコピーを作成し、`icomp`によって決定された新しい偏光基底に変換します。`icomp`の合法的な値とその意味：

  * 1 => EθおよびEϕ
  * 2 => ERHCPおよびELHCP
  * 3 => EhおよびEv（Ludwig 3 coおよびcx）
