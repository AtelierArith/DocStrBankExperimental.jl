```
path = localpath(title, checkfun, isfolder=false)
```

ローカルファイルまたはフォルダーへのパスを取得します（isfolderがtrueの場合）。ユーザーが以前に指定していない場合は、確認を求めます。checkfun(path)が実行され、trueの場合にのみパスが返されます。
