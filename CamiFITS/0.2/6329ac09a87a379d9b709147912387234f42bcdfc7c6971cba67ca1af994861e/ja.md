```
fits_copy(filnam1 [, filnam2="" [; protect=true]])
```

`filnam1`を`filnam2`にコピーします（必須の`.fits`拡張子付き） キー:

  * `protect::Bool`: 上書き保護
  * `msg::Bool`: ステータスメッセージを許可

#### 例:

```
julia> filnam = "foo.fits";

julia> fits_create("foo1.fits"; protect=false);

julia> fits_copy("foo1.fits", "foo2.fits"; protect=false);
'foo1.fits' was copied to 'foo2.fits'

julia> rm.(["foo1.fits", "foo2.fits"]);
```
