```
SimplifiedLCMC([categories])
```

A character frequency dataset: Lancaster Corpus for Mandarin Chinese, simplified terms only, based on simplified text corpus. See their [website](https://www.lancaster.ac.uk/fass/projects/corpus/LCMC/default.htm) for more details about the corpus.

The character frequency can be based only on selected categories (see `CJKFrequencies.LCMC_CATEGORIES` for valid  category keys and corresponding category names). Any invalid categories will be ignored.

## Examples

Loading all the categories:

```julia-repl
julia> charfreq(SimplifiedLCMC())
DataStructures.Accumulator{String,Int64} with 45411 entries:
  "一路…   => 1
  "舍得"   => 9
  "５８"   => 1
  "神农…   => 1
  "十点"   => 8
  "随从"   => 9
  "荡心…   => 1
  "尺码"   => 1
  ⋮      => ⋮
```

Or loading just a subset (argument can be any iterable):

```julia-repl
julia> charfreq(SimplifiedLCMC("ABEGKLMNR"))
DataStructures.Accumulator{String,Int64} with 35488 entries:
  "废…  => 1
  "蜷"  => 1
  "哇"  => 13
  "丰…  => 1
  "弊…  => 3
  "议…  => 10
  "滴"  => 28
  "美…  => 1
  ⋮    => ⋮
```

## Licensing/Copyright

Note: This corpus has some conflicting licensing information, depending on who is supplying the data.

The original corpus is provided primarily for non-profit-making research. Be sure to see the full [end user license agreement](https://www.lancaster.ac.uk/fass/projects/corpus/LCMC/lcmc/lcmc_license.htm).

Via the [Oxford Text Archive](https://ota.bodleian.ox.ac.uk/repository/xmlui/handle/20.500.12024/2474), this corpus is distributed under the [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) license.
