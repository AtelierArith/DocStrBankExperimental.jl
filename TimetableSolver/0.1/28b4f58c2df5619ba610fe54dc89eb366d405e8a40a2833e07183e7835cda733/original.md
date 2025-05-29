```
Timetable
```

Mutable type for representing a timetable.

# Constructors

  * `Timetable(numperiods::Vector{Int}, subjectcounts::SubjectCounts, teachers::Vector{Teacher}, division::Division)`

# Fields

  * `numperiods::Vector{Int}`: The number of periods in each row.
  * `subjectcounts::SubjectCounts`: The number of times subjects must occur in the timetable, in total.
  * `subjects::Vector{String}`: The subjects in the timetable.
  * `teachers::Vector{Teacher}`: The teachers in the timetable.
  * `subjectteachers::OrderedDict{String, Vector{Teacher}}`: The teachers teaching each subject.
  * `teacher_strs::OrderedDict{String, Teacher}`: The teachers' string representations mapped to objects.
  * `division::Division`: The division of the timetable.
  * `data::Vector{Vector{Period}}`: The timetable data, as a vector of vectors of periods.

# Notes

  * Only fields `numperiods`, `subjectcounts`, `teachers` and `division` are passed. The rest are inferred.
  * See the constructor for the same.
