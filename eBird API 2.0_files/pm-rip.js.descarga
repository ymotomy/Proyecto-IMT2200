(function () {
  try {
    const url = document.getElementById('pm-rip').getAttribute('data-url'),
      docCollectionId = document.getElementById('pm-rip').getAttribute('data-collection-id');

    let urlObj = {
      category: 'documenter',
      action: 'rip_click',
      entitytype: 'documentation',
      entityid: docCollectionId,
      property: 'postman-web',
      type: 'events-general'
    };

    urlObj = JSON.stringify(urlObj);

    const base64EncodedUrlObj = btoa(urlObj);
    window.addEventListener('load', () => {
      try {
        const buttons = document.getElementsByClassName('postman-run-button');
        if (buttons) {
          for (let i = 0; i < buttons.length; ++i) {
            buttons[i].addEventListener("click", async () => {
              fetch(url + '/events', {
                method: 'POST',
                body: base64EncodedUrlObj
              })
            });
          }
        }
      }
      catch (err) {
        if (window.Raven)
          window.Raven.captureException(err)
      }
    })
  }
  catch(err) {
    if (window.Raven)
      window.Raven.captureException(err)
  }
})();
