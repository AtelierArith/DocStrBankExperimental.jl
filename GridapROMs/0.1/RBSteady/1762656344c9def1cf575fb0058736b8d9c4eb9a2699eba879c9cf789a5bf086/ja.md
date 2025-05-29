```
load_operator(dir,feop::ParamOperator;kwargs...) -> RBOperator
```

FE演算子`feop`を与えると、ディレクトリ`dir`に保存されているその縮小版をロードします。縮小演算子が以前にファイルに保存されていない場合はエラーをスローします。
