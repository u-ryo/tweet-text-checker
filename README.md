# tweet-text-checker

## What's this?
Count the number of characters in your Tweet text for Twitter using the [official library](href="https://github.com/twitter/twitter-text).

## Why did I make this?
Recently I found that it's complicated how to count the twitter text length. Basically the limit is 280-characters but CJK(Chinese, Japanese, Korean) are counted as 2 characters, the URL string is always 23 (even if the URL string is longer / shorter than 23).
The Twitter.com offers the [official library](https://github.com/twitter/twitter-text) to count but I can't find any counting service using the official library. It's true that the twitter text overflow isn't a so big problem for the personal use, but not for the firm using it as advertising. I'm just wondering why the Twitter.com does offer just a library, not as a service.

## You can try
You can try through [this URL](https://cdn.jsdelivr.net/gh/u-ryo/tweet-text-checker@master/) or using `groovy` like below on the command line with [Docker](https://docker.com).

```groovy
$ docker run --rm -it groovy groovysh
groovy:000> groovy.grape.Grape.grab(group:'com.twitter.twittertext',module:'twitter-text',version:'3.0.1')
===> null
groovy:000> com.twitter.twittertext.TwitterTextParser.parseTweet('''\
groovy:001> This is a sample tweet.
groovy:002> New line is OK.
groovy:003> 日本語でもOKです！Japanese are also countable.
groovy:004> https://some.url.com/looooooooooooooooong_name.jpg URL is always 23 characters.
groovy:005> Please try to make the URL above longer.''').dump()
===> <com.twitter.twittertext.TwitterTextParseResults@a65091f weightedLength=180 permillage=642 isValid=true displayTextRange=com.twitter.twittertext.Range@1686 validTextRange=com.twitter.twittertext.Range@1686>
```
