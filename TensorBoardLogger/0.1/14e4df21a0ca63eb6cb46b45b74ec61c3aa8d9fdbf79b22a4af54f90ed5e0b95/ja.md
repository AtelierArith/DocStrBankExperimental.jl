log*image(logger, name, obj; [step=current*step])

オブジェクトをPNG形式でレンダリングし、タグ`name`を付けてTensorBoardに画像として送信します。`showable("image/png", obj)`がtrueである必要があります。
