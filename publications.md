---
title: Publications
layout: page
permalink: /publications/

---

{% assign publicationsByYear = site.data.publications | where_exp: "publication", "publication.id_iris != nil" | group_by: "year" | sort: "name" | reverse %}

<div>
  {% for year in publicationsByYear %}
      {% assign yearn = year.name | plus:0 %}
      {% if yearn >= 2025 %}
          <h1>{{ year.name }} <small>({{ year.items.size }})</small></h1>
          {% include list-publications.html source=year.items sort_by="id_iris" sort_reverse=true %}
      {% endif %}
  {% endfor %}

  <h1>Past Publications</h1>
  <p>SaFEWaRe was formed in 2025. Here follows the list of publications by SaFEWaRe members released before that date.</p>
  {% for year in publicationsByYear %}
      {% assign yearn = year.name | plus:0 %}
      {% if yearn < 2025 %}
          <h2>{{ year.name }} <small>({{ year.items.size }})</small></h2>
          {% include list-publications.html source=year.items sort_by="id_iris" sort_reverse=true %}
      {% endif %}
  {% endfor %}
</div>