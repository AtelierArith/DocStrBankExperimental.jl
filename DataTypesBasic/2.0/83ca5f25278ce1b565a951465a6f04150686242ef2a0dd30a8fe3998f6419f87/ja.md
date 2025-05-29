```
flip_left_right(Const(1)) == Identity(1)
flip_left_right(Identity(:whatever)) == Const(:whatever)
```

左右を入れ替えます。つまり、ConstであったものはIdentityになり、その逆も同様です。
