```
gmtconvert(cmd0::String="", arg1=nothing, kwargs...)
```

Convert, Paste, and/or Extract columns from data tables

## Parameters

  * **A** | **hcat** :: [Type => Str | []]

    The records from the input files should be pasted horizontally, not appended vertically [Default].
  * **C** | **n_records** :: [Type => Str]  $Arg = [+lmin][+umax][+i]$

    Only output segments whose number of records matches your given criteria:
  * **D** | **dump** :: [Type => Str | []]   $Arg = [template[+oorig]]$

    For multiple segment data, dump each segment to a separate output file.
  * **E** | **first_last** :: [Type => Str | []]   $Arg = [f|l|m|Mstride]$

    Only extract the first and last record for each segment of interest.
  * **F** | **conn_method** :: [Type => Str | []]   $Arg = [c|n|r|v][refpoint]$

    Alter the way points are connected (by specifying a scheme) and data are grouped (by specifying a method).
  * **I** | **invert** | **reverse** :: [Type => Str | Bool]      $Arg = [tsr]$

    Invert the order of items, i.e., output the items in reverse order, starting with the last   and ending up with the first item.
  * **L** | **list_only** :: -[Type => Bool]

    Only output a listing of all segment header records and no data records.
  * **N** | **sort** :: [Type => Str | Number]      $Arg = [-|+]col$

    Numerically sort each segment based on values in column col.
  * **Q** | **segments** :: [Type => Str]      $Arg =  [~]selection$

    Only write segments whose number is included in $selection$ and skip all others.
  * **S** | **select_hdr** :: [Type => Str]      $Arg =  [~]”search string” or [~]/regexp/[i]$

    Only output those segments whose header record contains the specified text string.
  * **T** | **suppress** | **skip** :: [Type => Str | []]    $Arg = [h|d]$

    Suppress the writing of certain records on output. Append h to suppress segment headers   [Default] or d to suppress duplicate data records. Use T=:hd to suppress both types of records.
  * **W** | **word2num** :: [Type => Str | []]      $Arg = [+n]$

    Attempt to gmtconvert each word in the trialing text to a number and append such values   to the numerical output columns.
  * **Z** | **transpose** :: [Type => Str | []]      $Arg =  [first][:last]$

    Limit output to the specified record range. If first is not set it defaults to record 0   (very first record) and if last is not set then it defaults to the very last record.

To see the full documentation type: $@? gmtconvert$
