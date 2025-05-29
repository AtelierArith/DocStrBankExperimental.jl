イテレータに対応するq-gramを返します。イテレータがStringの場合、q-gramはSubStringです。

### 引数

  * `s` イテレータ
  * `q::Integer`: q-gramの長さ

## 例

```julia
for x in qgrams("hello", 2)
	println(x)
end
```
