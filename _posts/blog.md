---
layout: post
title: Wikipedia Recommendation System 
subtitle: Using MongoDB vector search
<!--gh-repo: daattali/beautiful-jekyll-->
<!--gh-badge: [star, fork, follow]-->
tags: [Mongo DB]
comments: true
mathjax: true
author: Shruti Kulkarni
---

I learned about NoSQL in my first class of Spring'25 and I was fascinated by MongoDB. I found it refreshing to work with schemaless data with no rigid structure that typical relational database management systems (RDBMSs) abide by.
I was working with a team that was extremely enthusiastic about working with Wikipedia data. I'll admit I was confused by the excitement over a website that I hadn't used since middle school, but the idea of using MongoDB to create a recommendation system drew me in. 
Adam Gent, in particular, was a passionate proponent of this idea and worked on embedding wikipedia articles before storing them into a GCS (Google Cloud Storage) bucket. He subsequently loaded the articles each represented by a unique vector onto Mongo Atlas. 
Here's what the data looked like:

![Wikipedia Data](https://beautifuljekyll.com/assets/img/wiki_data.png){: .mx-auto.d-block :}


As you can see, each article has a title and a vector embedding which represent the article content using a SentenceTransformer model. 
SentenceTransformer converts the text into a dense vector representation, capturing the semantic meaning of the words and sentences excluding stop words and punctuation.
The vector embeddings help in comparing articles more effectively. Therefore, articles with similar vector embeddings are represented by vectors that are close to each other in the vector space, indicating that the articles share similar content. 

Now to create a recommendation system, we wanted to suggest five articles similar to the one the reader is currently viewing. It proved taxing to compare vectors on MongoDB using regular indexing syntax. extemely taxing task if we wanted to  Mongo Atlas has a neat feature called vector search


{: .box-success}
This is a demo post to show you how to write blog posts with markdown.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](https://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/tables/etc.<br/>I also encourage you to look at the [code that created this post](https://raw.githubusercontent.com/daattali/beautiful-jekyll/master/_posts/2020-02-28-sample-markdown.md) to learn some more advanced tips about using markdown in Beautiful Jekyll.

**Here is some bold text**

## Here is a secondary heading

[This is a link to a different site](https://deanattali.com/) and [this is a link to a section inside this page](#local-urls).

Here's a table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

You can use [MathJax](https://www.mathjax.org/) to write LaTeX expressions. For example:
When \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c = 0\\) and they are $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

How about a yummy crepe?

![Crepe](https://beautifuljekyll.com/assets/img/crepe.jpg)

It can also be centered!

![Crepe](https://beautifuljekyll.com/assets/img/crepe.jpg){: .mx-auto.d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.

## Local URLs in project sites {#local-urls}

When hosting a *project site* on GitHub Pages (for example, `https://USERNAME.github.io/MyProject`), URLs that begin with `/` and refer to local files may not work correctly due to how the root URL (`/`) is interpreted by GitHub Pages. You can read more about it [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). To demonstrate the issue, the following local image will be broken **if your site is a project site:**

![Crepe](/assets/img/crepe.jpg)

If the above image is broken, then you'll need to follow the instructions [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). Here is proof that it can be fixed:

![Crepe]({{ '/assets/img/crepe.jpg' | relative_url }})
