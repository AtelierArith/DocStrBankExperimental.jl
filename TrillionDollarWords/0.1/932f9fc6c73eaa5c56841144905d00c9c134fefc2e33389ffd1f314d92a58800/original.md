```
load_all_sentences()
```

Load the dataset with all sentences from the artifact. This is the complete dataset with sentences from press conferences, meeting minutes, and speeches. 

  * The `sentence_id` column is the unique identifier of the sentence.
  * The `doc_id` column is the unique identifier of the document.
  * The `date` column is the date of the event.
  * The `event_type` column is the type of event (meeting minutes, speech, or press conference).
  * The labels in `label` are predicted by the model proposed in the paper.

> We use the RoBERTa-large model finetuned on the combined data to label all the filtered sentences in the meeting minutes, speeches, and press conferences.


  * The `sentence` column is the sentence itself.
  * The `score` column is the softmax probability of the label.
  * The `speaker` column is the speaker of the sentence (if applicable).
