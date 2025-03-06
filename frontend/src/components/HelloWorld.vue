<template>
  <div>
    <!-- Header -->
    <header class="header py-5 py-md-6">
      <div class="container">
        <div class="row align-items-center justify-content-between">
          <div class="col-md-7 text-center text-md-start mb-4 mb-md-0">
            <h1 class="display-4 fw-bold">{{ personalInfo.name }}</h1>
            <h2 class="h3 text-secondary">{{ personalInfo.title }}</h2>
          </div>
          <div class="col-md-5 text-center text-md-end">
            <a :href="personalInfo.github" target="_blank" class="btn btn-light btn-circle mx-1">
              <i class="fab fa-github"></i>
            </a>
            <a :href="personalInfo.twitter" target="_blank" class="btn btn-light btn-circle mx-1">
              <i class="fab fa-twitter"></i>
            </a>
            <a :href="personalInfo.linkedin" target="_blank" class="btn btn-light btn-circle mx-1">
              <i class="fab fa-linkedin-in"></i>
            </a>
          </div>
        </div>
      </div>
    </header>

    <!-- About Section -->
    <section class="py-5">
      <div class="container">
        <div class="card shadow-sm">
          <div class="card-body p-4 p-md-5">
            <h2 class="card-title h3 mb-4 text-primary">About Me</h2>
            <p class="card-text mb-4">{{ personalInfo.about }}</p>
            <div class="d-flex flex-wrap">
              <span v-for="skill in personalInfo.skills" :key="skill" 
                    class="badge bg-light text-primary me-2 mb-2 py-2 px-3">
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section class="py-5 bg-light">
      <div class="container">
        <h2 class="h3 mb-4 text-primary">Work Experience</h2>
        
        <div class="row g-4">
          <div v-for="(job, index) in experience" :key="index" class="col-12">
            <div class="card shadow-sm h-100 hover-shadow">
              <div class="card-body p-4">
                <div class="d-md-flex justify-content-between mb-3">
                  <h3 class="h5 fw-bold">{{ job.company }}</h3>
                  <span class="text-primary">{{ job.period }}</span>
                </div>
                
                <div class="mb-3">
                  <span v-for="characteristic in job.characteristics" :key="characteristic"
                        class="badge bg-secondary-subtle text-secondary me-2 mb-2">
                    {{ characteristic }}
                  </span>
                </div>
                
                <div class="mb-3">
                  <h4 class="h6 fw-bold">Role: {{ job.role }}</h4>
                  <p class="text-muted">{{ job.description }}</p>
                </div>
                
                <div>
                  <span v-for="tech in job.technologies" :key="tech"
                        class="badge bg-primary-subtle text-primary me-2 mb-2">
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="py-5 text-center">
      <div class="container">
        <h2 class="h3 mb-4 text-primary">Get In Touch</h2>
        <p class="text-muted mb-4 mx-auto" style="max-width: 600px;">
          Interested in working together? Feel free to reach out to discuss potential opportunities.
        </p>
        <a href="mailto:contact@example.com" class="btn btn-primary px-4 py-2">
          <i class="far fa-envelope me-2"></i> Contact Me
        </a>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-dark text-white py-4 text-center">
      <div class="container">
        <p class="mb-0">© {{ new Date().getFullYear() }} {{ personalInfo.name }}. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'PortfolioPage',
  data() {
    return {
      personalInfo: {
        name: 'Your Name',
        title: 'Full Stack Developer',
        github: 'https://github.com/yourusername',
        twitter: 'https://twitter.com/yourusername',
        linkedin: 'https://linkedin.com/in/yourusername',
        about: 'I am a passionate full-stack developer with over 7 years of experience building web applications. I specialize in Vue.js, Node.js, and cloud infrastructure. My approach combines technical excellence with a deep understanding of user needs to create efficient, scalable, and intuitive solutions.',
        skills: ['Vue.js', 'React', 'Node.js', 'TypeScript', 'AWS', 'Docker', 'GraphQL', 'Bootstrap']
      },
      experience: [
        {
          company: 'TechNova Solutions',
          period: 'Jan 2022 - Present',
          characteristics: ['Enterprise SaaS', 'Fintech', 'Remote-first'],
          role: 'Senior Full Stack Engineer',
          description: 'Leading development of core financial services platform using Vue.js and Node.js microservices architecture. Implementing CI/CD pipelines and mentoring junior developers.',
          technologies: ['Vue 3', 'TypeScript', 'Node.js', 'MongoDB', 'AWS', 'Docker']
        },
        {
          company: 'GrowthLabs',
          period: 'Mar 2019 - Dec 2021',
          characteristics: ['Early-stage Startup', 'E-commerce Platform', 'Hybrid Work'],
          role: 'Frontend Developer',
          description: 'Developed responsive and interactive user interfaces for an e-commerce analytics platform. Collaborated with UX designers to implement pixel-perfect designs and optimize performance.',
          technologies: ['Vue 2', 'Vuex', 'SCSS', 'Jest', 'Webpack', 'GraphQL']
        },
        {
          company: 'Digital Architects Inc.',
          period: 'Jun 2017 - Feb 2019',
          characteristics: ['Digital Agency', 'Client Services', 'On-site'],
          role: 'Junior Web Developer',
          description: 'Built websites and web applications for various clients across multiple industries. Worked in an agile team to deliver projects on tight deadlines.',
          technologies: ['JavaScript', 'React', 'PHP', 'MySQL', 'WordPress', 'Bootstrap']
        }
      ]
    };
  }
}
</script>

<style>
/* 기본 스타일 */
.header {
  background: linear-gradient(to right, #5e60ce, #6930c3);
  color: white;
}

.btn-circle {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  margin: 5px;
  font-size: 1.2rem;
}

.hover-shadow {
  transition: box-shadow 0.3s ease;
}

.hover-shadow:hover {
  box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.15) !important;
}

/* 반응형 조정 */
@media (max-width: 768px) {
  .btn-circle {
    width: 40px;
    height: 40px;
    font-size: 1rem;
  }
}
</style>