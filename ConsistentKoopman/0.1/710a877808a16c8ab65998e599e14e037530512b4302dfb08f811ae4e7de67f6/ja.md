```
delayembed(X, numdelays::Int)

データの遅延埋め込み、次のように返すべきです
Xemb: ((numdelays)⋅n) × (m - numdelays - 1) データ配列

# '' は以下のように機能するようです：
# testMat = [1 2 3 4 5 6 ; 7 8 9 10 11 12 ; 13 14 15 16 17 18];
# k = 0, 1, 2, 3
# delayembed(testMat,k)
# delayembed(testMat,0) == testMat '' 

引数
=================
- X: n × m データ配列、n 空間点と m 時間点を持つ
- numdelays: 整数、遅延の数（q = 1 が一貫性のために遅延なしであるべきです）
```
