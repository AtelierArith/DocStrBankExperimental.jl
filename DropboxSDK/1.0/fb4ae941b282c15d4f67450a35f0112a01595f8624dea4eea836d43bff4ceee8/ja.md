```
struct Authorization
    access_token::String
end
```

アクセストークンを含みます。ほとんどすべてのDropbox API関数は、そのようなトークンを必要とします。アクセストークンはパスワードのようなものであり、同じ注意を払って扱うべきです。
