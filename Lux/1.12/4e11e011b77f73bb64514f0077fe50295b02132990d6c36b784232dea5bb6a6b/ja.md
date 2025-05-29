```
RepeatedLayer(model; repeats::Val = Val(10), input_injection::Val = Val(false))
```

`model`を`repeats`回数だけ反復的に適用します。初期入力は、`input_injection = Val(true)`の場合にモデルに繰り返し渡されます。このレイヤーは計算を展開しますが、意味的には次のように同じです：

  * `input_injection = Val(false)`

```julia
res = x
for i in 1:repeats
    res, st = model(res, ps, st)
end
```

  * `input_injection = Val(true)`

```julia
res = x
for i in 1:repeats
    res, st = model((res, x), ps, st)
end
```

`repeats`は`20`未満の合理的な数であることが期待されており、それを超えると勾配のコンパイル時間が不当に高くなる可能性があります。

## 引数

  * `model`は`AbstractLuxLayer`でなければなりません

## キーワード引数

  * `repeats`: モデルを適用する回数
  * `input_injection`: `true`の場合、出力とともに入力がモデルに渡されます

# 拡張ヘルプ

## 入力

  * `x`: 上記のように説明された入力

## 戻り値

  * 出力は上記のように計算されます
  * `model`の更新された状態

## パラメータ

  * `model`のパラメータ

## ステート

  * `model`の状態

```
