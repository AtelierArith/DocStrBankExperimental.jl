```
threadcall_apriltag_detector_detect(tag_detector, image)
```

*実験的*に別スレッドで apriltag*detector*detect を呼び出すには、実験的な `@threadcall` を使用します。画像からタグを検出し、apriltag*detection*t* の配列を返します。apriltag*detections*destroy を使用して配列とそれに含まれる検出を解放するか、detection*destroy と zarray*destroy を自分で呼び出すことができます。
