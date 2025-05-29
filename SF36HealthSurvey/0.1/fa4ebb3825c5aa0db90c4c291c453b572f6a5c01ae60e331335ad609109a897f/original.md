```
sf36(v; version = :v1)
```

Calculate SF36 results for vector of answers `v`.

version keyword:

  * `:v1` - General US population (Ware, John & MA, Kosinski & Keller, S.D.. (1993). SF-36 Physical and Mental Health Summary Scales: a User's Manual. 8. 23-28.)
  * `:v2` - Correlated scores (Grassi, M. and Nucera, A. (2010), Dimensionality and Summary Measures of the SF-36 v1.6: Comparison of Scale- and Item-Based Approach Across ECRHS II Adults Population. Value in Health, 13: 469-478.)

Vector `v`:

1,33:36 - General Health(GH) - 1, 11a:11d

3:12 - Physical functioning (PF) - 3a:3j

13:16 - Role-Physical Functioning (RP) - 4a:4d

17:19 - RoleEmotional (RE) - 5a:5c

20,32 - Social Functioning (SF) - 6,10

21,22 - Bodily pain (BP) - 7,8

24:26,28,30 - Mental Health (MH) - 9b:9d, 9f, 9h

23,27,29,31 - Vitality (VT) - 9a, 9e, 9g, 9i 
