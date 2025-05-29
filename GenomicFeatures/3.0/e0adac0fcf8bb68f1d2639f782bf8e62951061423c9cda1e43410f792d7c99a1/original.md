```
coverage(intervals)
```

Compute the coverage of a collection of intervals and return an `GenomicIntervalCollection` that contains run-length encoded coverage data.

For example, given intervals like:

```
[------]     [------------]
   [---------------]
```

This function would return a new set of disjoint intervals with annotated coverage like:

```
[1][-2-][-1-][--2--][--1--]
```

# Example

```jldoctest
julia> intervals = [
           GenomicInterval("chr1", 1, 8),
           GenomicInterval("chr1", 4, 20),
           GenomicInterval("chr1", 14, 27)];

julia> coverage(intervals)
GenomicIntervalCollection{GenomicInterval{UInt32}} with 5 intervals:
  chr1:1-3  .  1
  chr1:4-8  .  2
  chr1:9-13  .  1
  chr1:14-20  .  2
  chr1:21-27  .  1
```
