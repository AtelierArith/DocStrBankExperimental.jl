Return an iterator corresponding to the the q-gram of an iterator.  When the iterator is a String, qgrams are SubStrings.

### Arguments

  * `s` iterator
  * `q::Integer`: length of q-gram

## Examples

```julia
for x in qgrams("hello", 2)
	println(x)
end
```
