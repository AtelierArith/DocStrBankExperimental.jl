init(T::Type; ...)

Same as init, except that the literals should now be of type T.

push! and append! add one, respectively many clauses, each of which is an enumerable object consisting of objects of type T or Pair{T,Bool} to express negated variables.
