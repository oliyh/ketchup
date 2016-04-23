# ketchup

Missed a conversation? Ketchup will instantly summarise it in a few sentences,
letting you catch up in seconds and join in!

## Usage

Todo: Slack / Twitter / IRC / Google groups etc

## Examples

```
(ketchup [{:from "marc" :message "did anyone see the game last night?"}
          {:from "kim" :message "what an epic game!"}
          {:from "jarvis" :message "wrong result, they didn't deserve that last minute penalty"}
          {:from "kim" :message "i thought they did, it was obviously against the rules"}])

;; => "marc, kim and jarvis talked about the epic game last night, and kim disagreed with jarvis about the last minute penalty"
```

## To do

Key features:
* Identify distinct conversations
* Identify the participants in each conversation
* Derive a topic for each conversation
* Derive a sentiment from each participant about the topic
* Identify sub-topics and sentiment from each user

### Implementation ideas

* Core engine should identify distinct conversations
 * Any gaps between messages, say 5 minutes or longer, could be construed as ending a conversation
  * Unless the topic appears to be the same
* Conversation topic could be one of the most frequently used words
 * [Zipfs law](https://en.wikipedia.org/wiki/Zipf%27s_law) seems to be most relevant here
 * Extra weighting perhaps in the first message of the conversation as that is likely to set the topic
 * Markov chains will help determine topics from related words - this will be useful to persist across conversations
* Needs a learning mechanism
* Would be useful if it could integrate with various sources like Slack, Twitter, IRC, Google groups etc
* The users involved in a conversation should have their own contributions summarised
* Users referenced more should have their contributions weighted more
* ElasticSearch would be good at analysing term frequency and storing Markov chains

## License

Copyright © 2016 oliyh

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
