<template>
  <div class="text-gray-800 font-sans flex flex-col py-8 px-16">
    <h1 class="mx-auto font-bold text-4xl">Saumya Singhal</h1>
    <hr class="mt-2" />
    <div class="flex pt-4 gap-8 flex-row px-4">
      <div class="flex grow flex-col gap-2">
        <div>
          <h2>Education</h2>
          <div :key="key" v-for="(ed, key) in education">
            <h3 class="mt-1 gap-1 flex flex-row mb-[2px] text-xs">
              <span class="font-semibold">{{ ed.name }}</span> <span v-if="ed.desc" class="text-emerald-500">•</span> <span>{{ed.desc}}</span>
              <span class="italic ml-auto"
                >{{ ed.start }} - {{ ed.end || "Present" }}</span
              > 
            </h3>
            <p class="text-[0.6rem] font-light">{{ ed.body }}</p>
          </div>
        </div>
        <div>
          <h2>Leadership</h2>
          <div :key="key" v-for="(l, key) in leadership">
            <h3 class="mt-1 flex flex-row mb-[2px] text-xs gap-1">
              <span class="font-semibold">{{ l.name }} </span> <span class="text-emerald-500">•</span> <span>{{l.position}}</span>
              <span class="italic ml-auto"
                >{{ l.start }} - {{ l.end || "Present" }}</span
              >
            </h3>
            <p class="text-[0.6rem] font-light">{{ l.body }}</p>
          </div>
        </div>
        <div>
          <h2>Projects</h2>
          <div :key="key" v-for="(p, key) of projects">
            <h3 class="mt-1 flex flex-row mb-[2px] text-xs gap-1">
              <span class="font-semibold">{{ p.name }} </span> <span class="text-emerald-500">•</span> <span>{{p.desc}}</span>
              <span class="italic ml-auto"
                >{{ p.start }} - {{ p.end || "Present" }}</span
              >
            </h3>
            <p class="text-[0.6rem] font-light">{{ p.body }}</p>
          </div>
        </div>
      </div>
      <div class="flex gap-2 max-w-[15rem] flex-col">
        <div>
          <h2>Contact</h2>
          <div class="text-xs flex flex-col gap-1">
          <p>realsaumya@gmail.com</p>
          <p>(510)-945-8901</p>
          <p>832 Loma Verde Avenue<br/>Palo Alto, CA, 94303</p>
          <p>github.com/saumyasinghal747</p>
          </div>
        </div>
        <div>
          <h2>Skills</h2>
          <div class="text-xs">{{skills}}</div>
        </div>
        <div>
        <h2>Awards</h2>
        <div class=" text-gray-800 text-xs max-w-none">
          <ul class="flex flex-col gap-1">
            <li class="text-xs" :key="adx" v-for="(a, adx) of awards">
              {{ a }}
            </li>
          </ul>
        </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData({ $content }) {
    return {
      education: await $content("education")
        .fetch()
        .then((e) => e.education),
      awards: await $content("awards")
        .fetch()
        .then((e) => e.awards),
      leadership: await $content("leadership")
        .fetch()
        .then((e) => e.leadership),
      projects: await $content("projects")
        .fetch()
        .then((e) => e.projects),
      skills: await $content("skills")
        .fetch()
        .then((e) => e.skills),
    };
  },
};
</script>
