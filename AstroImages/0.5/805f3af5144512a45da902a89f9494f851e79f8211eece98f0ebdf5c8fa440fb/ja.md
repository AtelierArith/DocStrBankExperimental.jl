```
wcs(img)
```

WCS.jlからのWorld Coordinate System WCSTransformオブジェクトのリストを計算して返します。結果は最初の呼び出しの後にキャッシュされるため、以降の呼び出しは高速です。WCSヘッダーを変更すると、このキャッシュは自動的に無効になりますので、ユーザーはWCSTransformオブジェクトを保持するのではなく、毎回`wcs(...)`を呼び出すべきです。
