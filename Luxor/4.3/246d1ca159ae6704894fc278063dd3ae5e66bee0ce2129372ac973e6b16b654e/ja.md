```
circlecircleinnertangents(circle1center::Point, circle1radius, circle2center::Point, circle2radius)
```

2つの円の内接接線を見つけます。これらは、1つの円をすり抜けてもう1つの円に触れる接線です。

4つの点を返します：円1の接点1、円2の接点1、円1の接点2、円2の接点2。

内接接線が見つからない場合（例えば、円が重なっているとき）は `(O, O, O, O)` を返します。

外接接線を見つけるには `circlecircleoutertangents()` を使用してください。
