```
band(cmd0::String="", arg1=nothing; width=0.0, envelope=false, kwargs...)
```

線の周りに対称または非対称のバンドをプロットします。バンドが色で塗りつぶされていない場合、デフォルトではエンベロープのアウトラインのみがプロットされます。

例: 幅0.1の緑のバンドを持つsinc関数をプロットします（sinc線の上と下）

```
x = y = -10:0.11:10;
band(x, sin.(x)./x, width=0.1, fill="green@80", show=true)
```

または、同じですが関数を使用します

```
band(x->sin(x)/x, 10, width=0.1, fill="green@80", show=true)
```
