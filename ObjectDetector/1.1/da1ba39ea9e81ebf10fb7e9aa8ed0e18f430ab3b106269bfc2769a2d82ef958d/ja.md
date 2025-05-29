```
draw_boxes(img::Array, model::YOLO.Yolo, padding::Array, results)
draw_boxes!(img::Array, model::YOLO.Yolo, padding::Array, results)
```

各BBOX結果に対して、クラスカラーのボックスと信頼度ラベルを画像に描画します。`draw_boxes!`を使用する場合、`img`がカラー画像でない場合は、ボックスは黒でのみ描画されます。
