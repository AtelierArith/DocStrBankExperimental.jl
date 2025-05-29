使用法 `@update db[itemtoupdate] key1=val1 key2=val2 ..`

# 例

```jldoctest
julia> firstperson = first(db[Person[]]); firstperson.year_of_birth
1940
julia> @update db[firstperson] year_of_birth=1941; firstperson.year_of_birth
1941
```
