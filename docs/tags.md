---
layout: page
title: Tags
permalink: /tags/
---

<!-- Tag Cloud / Index Navigation -->
<div class="tag-cloud" style="margin-bottom: 30px;">
  {% assign tags = site.tags | sort %}
  {% for tag in tags %}
    {% assign tag_name = tag[0] %}
    {% assign tag_posts = tag[1] %}
    <a href="#{{ tag_name | slugify }}" style="font-size: 1.1em; margin-right: 15px; display: inline-block;">
      <strong>#{{ tag_name }}</strong> ({{ tag_posts.size }})
    </a>
  {% endfor %}
</div>

<hr>

<!-- Target Anchors and List of Posts -->
<div class="tag-sections">
  {% for tag in tags %}
    {% assign tag_name = tag[0] %}
    {% assign tag_posts = tag[1] %}
    
    <div id="{{ tag_name | slugify }}" class="tag-group" style="padding-top: 20px; margin-bottom: 20px;">
      <h2>#{{ tag_name }}</h2>
      <ul>
        {% for post in tag_posts %}
          <li>
            <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span> — 
            <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>
