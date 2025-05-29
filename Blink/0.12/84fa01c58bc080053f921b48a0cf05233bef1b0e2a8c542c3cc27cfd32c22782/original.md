```
js(win, expr::JSString; callback=false)
```

Execute the javscript in `expr`, inside `win`.

If `callback==true`, returns the result of evaluating `expr`.
