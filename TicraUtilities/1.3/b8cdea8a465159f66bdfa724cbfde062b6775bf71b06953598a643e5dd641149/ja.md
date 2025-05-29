```
convert_cut!(cut::Cut, icomp::Integer)
```

`cut`を`icomp`によって決定される新しい偏光基底に変換します。`icomp`の合法的な値とその意味：

  * 1 => EθおよびEϕ
  * 2 => ERHCPおよびELHCP
  * 3 => EhおよびEv（Ludwig 3 coおよびcx）
