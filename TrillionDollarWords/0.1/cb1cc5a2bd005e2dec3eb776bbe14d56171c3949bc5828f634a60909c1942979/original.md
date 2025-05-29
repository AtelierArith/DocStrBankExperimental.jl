```
load_training_sentences()
```

Load the dataset with training sentences from the artifact. This is a combined dataset containing sentences from press conferences, meeting minutes, and speeches.

  * The `sentence` column is the sentence itself.
  * The `year` column is the year of the event.
  * The labels in `label` are the manually annotated labels from the paper.
  * The `seed` column is the seed that was used to split the data into train and test set in the paper.
  * The `sentence_splitting` column indicates if the sentence was split or not (see the paper for details).
  * The `event_type` column is the type of event (meeting minutes, speech, or press conference).
  * The `split` column indicates if the sentence is in the train or test set.
